---
layout: post
title: C# Language Weirdness
date: 2015-02-07
comments: false
tags: [C#]
category: C#
---

When using and learning about a programming language you are bound to, at some point, learn about some oddities in the programming language. Recently, I (once again) stumbled across the *[What's the strangest corner case you've seen in C# or .NET?][SO - Corner]* question on [StackOverflow][SO] and I thought I would compile a list of some, of what I consider to be, surprising "features" of the C# *language*.

So here goes (in no particular order).

## 1. Comparison of nullable types

We all know about C#'s [Nullable Value Types][MSDN - Nullable], but what happens when we compare them? 

```csharp
int? nonNull = 1, isNull = null;

nonNull == isNull   // False - Makes sense
isNull == null      // True - Makes sense
nonNull == nonNull  // True - Makes sense
isNull < null       // False - Makes sense
isNull <= null      // False - Make.. Wait what? 
isNull <= isNull    // False - ...
```

For some (unknown to me) reason, comparing two nullable value types (whose value is null) with `<=` evaluate to false. It is false even though comparing with `==` evaluate to true. 

So apparently, a null nullable value type is *equal* to null, but it is not *below or equal* to null. 

## 2. Enums and method overloading
Let's assume we have this enum and these methods

```csharp
enum SomeEnum { One = 1 };

string MyMethod(SomeEnum myEnum) { return "ENUM"; }
string MyMethod(object myObject) { return "OBJECT"; }
```
And then we call those methods a few times and look at the response

```csharp
MyMethod(SomeEnum.One)        // "ENUM" - Obviously.
MyMethod("Some string")       // "OBJECT" - Obviously.
MyMethod(0)                   // "ENUM" - Okay..
MyMethod(Convert.ToInt32(0))  // "OBJECT" - Ehm..
MyMethod(1)                   // "OBJECT" - What?
```

What is the significance of 0 vs 1? 

The default value of an enum is the default value of its underlying type (in this case an integer), which is 0. In fact, since an enum's underlying type can only be integral types (except char), the default value for all enums is 0. Because of the way this is handled, 0 (as the only value) can be implicitly converted to any enum, which is why 0 and 1 does not call the same overload.
The reason why `Convert.ToInt32(0)` also calls the `object` overload is because [overload resolution][MSDN - Overload] happens at compile time, but the value returned from `Convert.ToInt32(0)` is not known by the compiler.

## 3. Default parameter values and overloading
This time we have the following classes:

```csharp
class Base
{
    public virtual string MyMethod(int i = 1)
    {
        return i + " Base";
    }
}

class Derived : Base
{
    public override string MyMethod(int i = 2)
    {
        return i + " Derived";
    }
}
```

What is the result of the following invocation of `MyMethod`?

```csharp
Base b = new Derived();
b.MyMethod();  // ??
```

There are two obvious possibilities: *"1 Base"* and *"2 Derived"*. Everybody who knows about how method overriding works in C#, will probably quickly figure out that it is the `MyMethod` from `Derived` that is being called. This might cause many people to think that the result will be *"2 Derived"*. 
Would you be surprised if I tell you that the result is *"1 Derived"*? The default value from the base class method is being used, even though it is the subclass's method that is being called.

Once again, it is a compile time vs run-time issue. Default parameter values are resolved at compile time while method override resolution is handled at run-time. 


<br />
That was a few cases that surprised me a bit when I learned about them. I might add more at some point. Until then, if you are interested, you can probably find more C# weirdness through Google. 

<!-- Bibliography -->

[SO]: http://stackoverflow.com "StackOverflow"
[SO - Corner]: http://stackoverflow.com/q/194484/1401257 "What's the strangest corner case you've seen in C# or .NET?"
[MSDN - Nullable]: https://msdn.microsoft.com/en-us/library/1t3y8s4s.aspx "Nullable Types (C# Programming Guide)"
[MSDN - Overload]: https://msdn.microsoft.com/en-us/library/aa691336%28v=vs.71%29.aspx "7.4.2 Overload resolution"
