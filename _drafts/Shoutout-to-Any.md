---
layout: post
title: Shout-out to 'Any()'
date: 2014-09-08
comments: true
tags: [C#, .NET]
---

I will use this first post to remind whoever reads this about a useful method in the *System.Linq* namespace in .NET. This method is apparently (for reasons unknown) often forgotten. I'm talking about [`IEnumerable<T>.Any<T>()`][MSDN - Any()] (and let's not forget its [overload][MSDN - Any(Func)] - I will refer to both as `Any()` throughout this post).

For those who don't know what that method does (and can't guess it based on its name), here is a quote from the documentation:

> *Determines whether a sequence contains any elements.*

And for the overload:

> *Determines whether any element of a sequence satisfies a condition.*

For some reason this method is often forgotten (or at least not used when it could have been), which result in code like this:

```csharp
1: someSequence.Count() > 0
2: someSequence.FirstOrDefault() != null 
3: someSequence.Where(x => x.SomeCondition).Count() > 0
4: someSequence.Where(x => x.SomeCondition).Count() == 0
```

and more like those. I have seen all of these statements in production code (usually as the condition to an if-statement). 

If `Any()` was used instead it would look like this: 

{% highlight C# %}

1,2: someSequence.Any()
3: someSequence.Any(x => x.SomeCondition)
4: !someSequence.Any(x => x.SomeCondition)

{% endhighlight %}

Isn't that simpler? (Some might like [`All<T>(..)`][MSDN - All()] better for the 3rd one. But still..)

By using `Any()` the code clearly tells the reader that we are only interested in whether the sequence contains any elements (that satisfy a condition). It shows *intent*.

`Any()` might also provide a performance increase compared to `Count()`. `Count()` is optimized when applied to a collection implementing the `ICollection` or `ICollection<T>` interface (in those cases it uses the property `Count` that is assumed to be faster). But if you have a sequence that do not implement either of those interfaces, `Count()` will go through *each element* in the sequence in order to count them. So if you have a very big sequence `Count()` might take quite a long time to execute, whereas `Any()` just have to see if there is an element (the overloaded `Any()` that accepts a predicate might have to through all the items also - but only if no elements in the sequence satisfy the predicate). 

So unless you have a good reason *not* to use `Any()` I endorse you to use it. 

<!-- Bibliography -->

[MSDN - All()]: http://msdn.microsoft.com/en-us/library/vstudio/bb548541(v=vs.110).aspx "MSDN: Enumerable.All<TSource> Method" 
[MSDN - Any()]: http://msdn.microsoft.com/en-us/library/bb337697.aspx "MSDN: Enumerable.Any<TSource> Method (IEnumerable<TSource>)"
[MSDN - Any(Func)]: http://msdn.microsoft.com/en-us/library/bb534972.aspx "MSDN: Enumerable.Any<TSource> Method (IEnumerable<TSource>, Func<TSource, Boolean>)"