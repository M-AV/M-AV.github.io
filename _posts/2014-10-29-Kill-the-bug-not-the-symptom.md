---
layout: post
title: Kill the bug! Don't hide it
date: 2014-10-29
comments: true
tags: 
category: Programming
---

Once or twice¹ in a developers life, will (s)he find a bug in an application (s)he is developing. It happens and it's (often) not that big of a deal. Most developers know that detecting and fixing bugs early is a shared responsibility, so few people will think less of the developer who committed the bug. What matters is how you fix it!

Whenever you have a bug in your application that you deem important enough to fix, you should do it right. You can probably get away with a quick hack to quickly make your clients happy, but at some point you should return and fix it properly! Once in a while (often actually) I see people "fix" a bug, but what they are really doing is hiding it (and that is rarely a good thing).

Let's say that one day you look through your error log and see that your application is throwing a lot of ``NullReferenceExceptions`` (or whatever the equivalent is in your programming language). From the stacktrace you can see it is happening in this function and the reason is that ``fancyObject`` is null.

{% highlight C# %}

public void DoSomething(string someString, object fancyObject, int aNumber)
{
	/*... some code ...*/
	fancyObject.InvokingMethod();
	/*... some more code ...*/
}

{% endhighlight %}

You have an important business meeting, so you ask you colleague (let's call him Carl John Johnson) to fix it. When you return from the meeting, Carl is happy to tell you that he fixed the bug with a simple and elegant solution, as can be seen here:

{% highlight C# %}

public void DoSomething(string someString, object fancyObject, int aNumber)
{
	if(fancyObject == null) { return; }
	/*... some code ...*/
	fancyObject.InvokingMethod();
	/*... some more code ...*/
}

{% endhighlight %}

The code no longer throws a ``NullReferenceException``, we didn't change the code much to fix this error, so surely this is a good fix. Right?

The problem with this "fix" is that it didn't fix anything. It prevents the application from throwing an exception, so we can no longer see that there is an error in the error log. The bug is hidden from us and just waiting to escalate into something more serious. *Why was ``fancyObject`` null in the first place?* 

Whenever ``DoSomething`` is called, the calling code expects ``DoSomething`` to *actually do something*. With Carls fix, we can no longer be sure that that something is being done. Worse, we are not being told whether it is being done or not. Carl shouldn't have tried to fix the error in this method. If he must do something to it I think he (probably) should have added *guard clauses*. 

{% highlight C# %}

public void DoSomething(string someString, object fancyObject, int aNumber)
{
	if(someString == null) { throw new ArgumentNullException("someString"); }
	if(fancyObject == null) { throw new ArgumentNullException("fancyObject"); }
	/*... the rest of the method ...*/
}

{% endhighlight %}

*But.. This doesn't fix the issue? It just causes different exception to be thrown. Why is this useful?* Because now the error we get is more meaningful. We are failing earlier and closer to the actual issue and it is a little bit clearer what happened. We still don't know why ``fancyObject`` is null, but we know that the issue is *not in this method*. The guard clauses clearly states that this method is not supposed to be called with null objects, so we need to figure out why it is. When we figure out why ``fancyObject`` is null, we find the real issue and we can take appropriate action (and thereby avoid calling ``DoSomething`` in the first place.)

There is a million reasons why ``fancyObject`` could be null and it doesn't really matter why it is (for this example). The point is, you should always try to track down the *source* of an issue and see if you can fix it from there. Don't hide the error as Carl John Johnson did and think everything is dandy. **Try to fix the code properly!**

These kind of fixes typically happens when we notice the issue far away from where the problem actually is. This is one of the reasons I'm a fan of [failing fast][Fail Fast - Jim Shore], where we try to force ourselves to notice (or force the application to tell us about) an error close to where the issue actually is.

I am well aware that sometimes these kind of fixes might actually be the right way to go. The problem is that sometimes it seems these kinds of fixes are the default solution. There is a very good chance that at some point you will have to fix the issue anyways, so why not fix it as early as possible? 

- 1. Roughly..


<!-- Bibliography -->

[Fail Fast - Jim Shore]: http://www.martinfowler.com/ieeeSoftware/failFast.pdf "Fail Fast - Jim Shore"
