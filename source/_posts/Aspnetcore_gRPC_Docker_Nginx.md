---
layout: post
title: Setting up gRPC in ASP.NET Core project using Docker and Nginx
date: 2020-09-05
comments: true
tags: [C#, .NET]
category: Programming
---

# Setting up gRPC in existing ASP<span>.NET Core project using Docker and Nginx

I have had dotnet API running on a Digital Ocean server for quite some time. The API is running in a Docker container along with a bunch of other containers. Nginx is used as a reverse proxy to route requests to the various containers. 
Recently, I had an idea for a project where I wanted to use gRPC. The plan was to add gRPC endpoints to the existing API project without having to change too much of the setup. 

It sounded like an easy task, but took more time than expected. This is how I did it.

## Step 1 - Add gPRC support to API

My first task was to add gRPC endpoints to the existing api and get it working locally.

I added the [gRPC for .NET](https://github.com/grpc/grpc-dotnet) NuGet packages from the gRPC authors.

Next I configured gRPC in the `ConfigureServices` method (Startup.cs) by calling `AddGrpc`:

```csharp
public void ConfigureServices(IServiceCollection services)
{       
    services.AddGrpc(opts => 
    {
        opts.EnableDetailedErrors = true;
    });
    services.AddControllers();
    ...
```

I set `EnableDetailedErrors` since I expected to be doing a bunch of debugging later on. For an application running in production, consider keeping this disabled.

### 1.1 Add a gRPC service to the API
I started out with a default "Greeter" service. I wanted to make sure everything was working before implementing the actual API I wanted. 

I added the `greet.proto` specification file to the API

```csharp
syntax = "proto3";

option csharp_namespace = "My.Namespace.Proto";
package greet;

service Greeter {
    rpc SayHello (HelloRequest) returns (HelloReply);
    rpc SayHellos (HelloRequest) returns (stream HelloReply);
}

message HelloRequest {
    string name = 1;
}

message HelloReply {
    string message = 1;
}
```

Since I want to use the streaming functionality of gRPC I added an endpoint that would stream responses to the client when invoked as well.

The file has to be referenced from the `.csproj` file. I added a reference to it right above my NuGet references:
```xml
<ItemGroup>
    <Protobuf Include="Proto\greet.proto" />

    <PackageReference Include="Grpc.AspNetCore" Version="2.30.0" />
    ...
```

After building the project a few times to trigger the automatic generation of `Greeter.GreeterBase`, I added the actual service logic to the project. The API logic is in the two methods. `SayHello` that just returns a single `HelloReply` and `SayHellos` which continuously sends out messages with a 1 second delay.  The code should be farily self-explanatory. 

```csharp
public class GreeterService : Greeter.GreeterBase
{
    private readonly ILogger _logger;

    public GreeterService(ILoggerFactory loggerFactory)
    {
        if (loggerFactory == null) { throw new ArgumentNullException(nameof(loggerFactory)); }

        _logger = loggerFactory.CreateLogger<GreeterService>();
    }

    public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
    {
        _logger.LogInformation($"Sending hello to {request.Name}");
        return Task.FromResult(new HelloReply { Message = "Hello " + request.Name });
    }

    public override async Task SayHellos(HelloRequest request, IServerStreamWriter<HelloReply> responseStream, ServerCallContext context)
    {
        var i = 0;
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var message = $"How are you {request.Name}? {++i}";
            _logger.LogInformation($"Sending greeting {message}.");

            await responseStream.WriteAsync(new HelloReply { Message = message });
            await Task.Delay(1000); // Gotta look busy
        }
    }
}
```

When all this is done, we need to register the endpoint. Back in the `Startup.cs` we call `MapGrpcService` in the `Configure` method to register the endpoints:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    // Some other calls here
    app.UseEndpoints(endpoints =>
    {
          endpoints.MapGrpcService<GreeterService>();
          endpoints.MapControllers();
    });
}
```

### 1.2 Create a gRPC client
At the same time I created a seperate project acting as a client for the API so I could test it. Nothing fancy, just a simple Console appliation using the same `.proto` specifications, with some code to call the endpoints:

```csharp
var httpClientHandler = new HttpClientHandler();
var channel = GrpcChannel.ForAddress("http://localhost:5001", new GrpcChannelOptions
{
      HttpClient = new HttpClient(httpClientHandler)
});
var client = new Greeter.GreeterClient(channel);
// Call simple endpoint
var reply = await client.SayHelloAsync(new HelloRequest { Name = "GreeterClient" });
Console.WriteLine("Greeting: " + reply.Message);

// Call streaming endpoint
var cts = new CancellationTokenSource();
cts.CancelAfter(TimeSpan.FromSeconds(3.5));
using (var call = client.SayHellos(new HelloRequest { Name = "GreeterClient" }, cancellationToken: cts.Token))
{
      try
      {
          await foreach (var message in call.ResponseStream.ReadAllAsync())
          {
              Console.WriteLine("Greeting: " + message.Message);
          }
      }
      catch (RpcException ex) when (ex.StatusCode == StatusCode.Cancelled)
      {
          Console.WriteLine(ex.ToString());
          Console.WriteLine("Stream cancelled.");
      }
}
```

### 1.3 Try it out
At this point I tried running the API and the client.. Aaaaaand.. It didn't work. I was still able to call all my REST endpoints, but got errors when calling the gRPC endpoints. I did manage to call the gPRC successfully.. if I removed the REST part. 

Eventually, I found a [StackOverflow post](https://stackoverflow.com/a/58662496/1401257) mentioning splitting the ports and setting one to HTTP1 and the other to HTTP2 (in `Program.cs`).

```csharp
webBuilder.ConfigureKestrel(options =>
{
    // gRPC
    options.ListenAnyIP(5001, o => o.Protocols = HttpProtocols.Http2);
    // HTTP
    options.ListenAnyIP(5000, o => o.Protocols = HttpProtocols.Http1); 
});
```

With this I was able to call the REST endpoints using port 5000 and gRPC using port 5001. Not entirely sure what logic makes this work though..

## Step 2 - Add Docker Support

With Visual Studio we can autogenerate a docker file to the project. I slightly modified the autogenerated one to expose the right ports and include my DTOs project. This will first build the project and then create a Docker image with a release build of the API.

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-buster-slim AS base
WORKDIR /app

EXPOSE 5000
EXPOSE 5001

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-buster AS build
WORKDIR /src
COPY ["My.Project.API/My.Project.API.csproj", "My.Project.API/"]
COPY ["My.Project.DTOs/My.Project.DTOs.csproj", "My.Project.DTOs/"]
RUN dotnet restore "My.Project.API/My.Project.API.csproj"
COPY . .
WORKDIR "/src/My.Project.API"
RUN dotnet build "My.Project.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "My.Project.API.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "My.Project.API.dll"]
```

### 2.1 - Run Image on Server
You can deploy a Docker image in many ways. Personally, I'm using Gitlab CI to deploy my project. I won't go into details about that here.

After deployment I started looking at the Nginx setup. It took me a while to figure it out. At one point I was doubting that the docker container was actually working as I expected. To test it, I used [grpc_cli](https://github.com/grpc/grpc/blob/master/doc/command_line_tool.md).

    > ./grpc_cli call 172.17.0.2:5001 greet.Greeter/SayHellos "name: 'world'" --protofiles=greet.proto
    > connecting to 172.17.0.2:5001
    > Received initial metadata from server:
    > date : Mon, 10 Aug 2020 00:04:05 GMT
    > server : Kestrel
    > message: "How are you world? 1"
    > message: "How are you world? 2"
    > message: "How are you world? 3"
    ... 

It was working! :)

## Step 3 - Nginx

Nginx has support for gRPC using the `grpc_pass` directive. It is relatively simple to use. The tricky part was figuring out what exactly the `location` should be in the Nginx config. In the end it turns out it should be set to the name of the service like this:

```nginx
upstream restapi {
    server apidocker:5000;
}
upstream grpcapi {
    server apidocker:5001;
}

# More unrelated configuration here

server {
    listen [::]:443 ssl http2;
    listen 443 ssl http2;
    
    # More unrelated configuration here

    location /api/ {
        proxy_pass http://restapi;
        proxy_set_header Host $host;
    }
    location /greet.Greeter/ {     # name is 'package.Service'
         grpc_pass grpc://grpcapi;
    }
}
```

Unfortunately, this means I have to add every new service to the Nginx configuration before it works. :( I don't think there is much I can do about that though. 

All that is needed from here is to update the url in the client and I am able to call both the REST and gRPC endpoints from anywhere.

```csharp
var channel = GrpcChannel.ForAddress("https://mydomain.com", new GrpcChannelOptions
{
    HttpClient = new HttpClient(httpClientHandler)
});
```

```
> Greeting: Hello GreeterClient
> Greeting: How are you GreeterClient? 1
> Greeting: How are you GreeterClient? 2
> Greeting: How are you GreeterClient? 3
> Greeting: How are you GreeterClient? 4
```

It works! Now I just need to implement the API I want.