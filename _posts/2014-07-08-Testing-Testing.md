---
layout: post
title: Reading List
date: 2014-04-08
comments: true
---

# Heading

## Heading

### Heading

#### Heading

##### Heading

###### Heading

> Beer and science go hand in hand

-

> Beer and science go hand in hand <br>
> <small> - ***How Beer Saved the World*** </small>

-

> Beer and science go hand in hand
>> Beer and science go hand in hand
>>> Beer and science go hand in hand <br>
>>> <small> - ***How Beer Saved the World*** </small>

-
## Programming Languages

1. ~ C# in Depth - Jon Skeet
  1. Sub item
2. CLR via. C# - Jeffrey Richter

## General programming:

    1. The Mythical Man-month - Frederick P. Brooks, Jr.

## Other things:

    1. ✓ The Tipping Point - Malcolm Gladwell
    2. ✓ You Must be Joking Mr. Feynman - Richard P. Feynman / Ralph Leighton

<!--mo re-->

{% highlight C# linenos %}
[Trait("Authentication", "Password doesn't match")]
public class PasswordDontMatch : TestBase {

  AuthenticationResult _result;
  public PasswordDontMatch() {
    var app = new Application("rob@tekpub.com", "password", "password");
    new Registrator().ApplyForMembership(app);

    _result = new Authenticator().AuthenticateUser(new Credentials { Email = "rob@tekpub.com", Password = "fixlesl" });

  }
}
{% endhighlight %}

Line `1` is not so important.. But the class needs to have the `public` modifier.

fdsafsad ads f: 

```csharp
// Comment 1
int i = 0; dfg fdsg fds gfdsg sfdg 
```


{% highlight C# %}
// Comment 1
int i = 0; dfg fdsg fds gfdsg sfdg 
{% endhighlight %}

fdsa fas fads 

Images..:
![Image of doom]({{ site.url }}/assets/imgs/dots.png)

![Image of doom]({{ site.url }}/assets/imgs/rss.ico "RSS ICON")

![Minion](http://octodex.github.com/images/minion.png "Minion")

[Other post]({{ site.url }}{% post_url 2014-07-08-Test-Test-Test %})


 **EM PHA _SIS_**.

Strikethrough: <del>Scratch this</del>?

| Ta        |     bl       |  es |
| ------------- |:-------------:| -----:|
| -----1,1----  | -----1,2---- | -----1,3---- |
| -----2,1----  | -----2,2----      |   -----2,3---- |
| -----3,1----  | -----3,2-jkljkljklfadsfsafadsfdsafdsafadsfdsajkljkljkljkljljklj---   |  -----3,3---- |
