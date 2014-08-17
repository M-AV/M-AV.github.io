---
layout: post
title: Reading List
date: 2014-04-08
comments: true
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus elementum, arcu vel ornare tincidunt, nibh diam volutpat libero, non feugiat diam lacus et lacus. Nunc feugiat ipsum id mi consequat auctor. Sed volutpat vel tortor et ultrices. Vestibulum vehicula ornare condimentum. Phasellus a nisi vel felis suscipit mattis id sit amet sem. Quisque sodales magna nibh, non sollicitudin sapien convallis eu. Etiam tincidunt ut eros bibendum lobortis. Fusce facilisis hendrerit turpis, eget suscipit augue tempus sed. Nulla tristique porta ligula, non blandit lectus.

Suspendisse scelerisque vehicula pretium. Ut sed aliquam tellus, quis fringilla lacus. Pellentesque nisl odio, dapibus ac venenatis blandit, congue molestie mauris. Cras eu convallis diam. Proin luctus tincidunt massa. Morbi luctus odio ut lorem fringilla pharetra. Maecenas sollicitudin fermentum adipiscing. Nam et erat eu orci volutpat aliquam. Proin pharetra elit est, a luctus mi sodales ut. Sed laoreet at metus et fermentum. Quisque bibendum, risus id fringilla luctus, ipsum massa dignissim est, nec imperdiet nisi felis non diam.

Qoute:

> Beer and science go hand in hand

> - - ***How Beer Saved the World***

-

> Beer and science go hand in hand. Beer and science go hand in hand. Beer and science go hand in hand. Beer and science go hand in hand. Beer and science go hand in hand. Beer and science go hand in hand. Beer and science go hand in hand. Beer and science go hand in hand. 

> - - ***How Beer Saved the World***


Sed convallis, est a viverra fermentum, sem dolor convallis odio, vel luctus lacus neque sed felis. Aenean id tempor justo. Aliquam mollis ante ut placerat auctor. Aliquam vestibulum erat enim, vitae sodales elit dictum vitae. Vestibulum adipiscing nibh lobortis, dapibus sapien eget, consectetur nulla. Vestibulum at adipiscing nisi. Curabitur consequat enim eros, id mollis mauris euismod sit amet. Sed felis justo, ornare nec risus et, laoreet pharetra augue. Praesent adipiscing neque ac sapien vulputate, ac sollicitudin eros vulputate. Praesent eget tellus non lectus venenatis ultricies. Curabitur id viverra enim, id lobortis nulla. Phasellus pretium nisl vel sapien imperdiet sollicitudin. Donec vel nisl felis.

Snatched the code samples here: http://www.wekeroad.com/2014/03/06/pragmatic-bdd/

Only used to have a code sample I can use when playing around with my code-blocks. 

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

Integer non semper est. Pellentesque cursus ante sapien, eget sodales mauris scelerisque id. Cras non magna sed dolor ullamcorper interdum. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Nunc odio enim, lobortis et justo ac, aliquam malesuada lorem. Quisque pretium urna sit amet suscipit suscipit. Proin sed quam ut dui tempor pharetra sed non sem.

```csharp
[Trait("Authentication", "Password doesn't match")]
public class PasswordDontMatch : TestBase {

  AuthenticationResult _result;
  public PasswordDontMatch() {
    var app = new Application("rob@tekpub.com", "password", "password");
    new Registrator().ApplyForMembership(app);

    _result = new Authenticator().AuthenticateUser(new Credentials { Email = "rob@tekpub.com", Password = "fixlesl" });

  }
}
```

Cras volutpat mauris nec tincidunt cursus. Maecenas vestibulum malesuada nisl, in vulputate nunc congue vel. Vivamus molestie, lorem sit amet auctor posuere, sapien dui ultrices leo, malesuada consectetur enim enim non orci. Praesent mattis sollicitudin massa mollis tincidunt. Sed lectus tortor, aliquet in libero ut, fermentum posuere tellus. Quisque ultrices mi vitae adipiscing lacinia. Quisque tempor turpis laoreet justo pretium, eget sodales eros porta. Cras eu tortor quis lorem porttitor tincidunt. Duis ac sagittis risus. Suspendisse vitae augue arcu.


# Programming Languages

    1. ~ C# in Depth - Jon Skeet
    2. CLR via. C# - Jeffrey Richter

# General programming:
    1. The Mythical Man-month - Frederick P. Brooks, Jr.

# Other things:
    1. ✓ The Tipping Point - Malcolm Gladwell
    2. ✓ You Must be Joking Mr. Feynman - Richard P. Feynman / Ralph Leighton