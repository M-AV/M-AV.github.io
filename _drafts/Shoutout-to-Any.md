---
layout: post
title: Shout-out to 'Any()'
date: 2014-09-06
comments: true
tags: [C#, .NET]
---

I will use this first post to remind whoever reads this about a useful method in the *System.Linq* namespace in .NET. This method is apparently (for reasons unknown) often forgotten. I'm talking about [`IEnumerable<T>.Any<T>()`][MSDN - Any()] (and let's not forget its [overload][MSDN - Any(Func)]).

For those who don't know what that method does (and can't guess it based on its name), here is a quote from the documentation:

> Determines whether a sequence contains any elements.

And for the overload:

> Determines whether any element of a sequence satisfies a condition.

For some reason this method is often forgotten (or at least not used when it could have been), which result in code like this:

{% highlight C# %}

1: someSequence.Count() > 0
2: someSequence.Where(x => x.SomeCondition).Count() > 0
3: someSequence.Where(x => x.SomeCondition).Count() == 0
4: someSequence.FirstOrDefault() != null 

{% endhighlight %}

and more like those. I have seen all of these statements in production code (usually as the condition to an if-statement). 

If `Any` was used instead it would look like this: 

{% highlight C# %}

1,4: someSequence.Any()
2: someSequence.Any(x => x.SomeCondition)
3: !someSequence.Any(x => x.SomeCondition)

{% endhighlight %}

Isn't that simpler? ([`All<T>(..)`][MSDN - All()] *might* be better suited for the 3rd one.)

By using `Any` the code clearly tells the reader that we are only interested in whether the sequence contains any elements (that satisfy a condition). It shows *intent*.

`Any` might also provide a performance increase compared to `Count`. `Count()` is optimized when applied to a collection implementing the `ICollection` or `ICollection<T>` interface (in those cases it uses the property `Count` that is assumed to be faster). But if you have a sequence that do not implement either of those interfaces, `Count()` will count the elements by going through *each element* in the sequence. So if you have a very big sequence `Count` might take quite a long time to execute, whereas `Any()` just have to see if there is an element (the overloaded `Any` that accepts a predicate might have to through all the items also). 

<br>
____
<br>

To those of you who made it this far: According to [this guy][Stackoverflow-Count-Slower], it seems that sometimes `Count()` is faster than `Any()`. If you ever find yourself in this situation and you choose to go with `Count()` because of the performance difference, please make it clear *why* you did that (e.g. write a comment). Someone might just refactor your code to use `Any` without knowing the potential performance hit.

None the less, `Any()` should be your default choice when you want to know whether a sequence contains elements.


<!-- Bibliography -->

[MSDN - All()]: http://msdn.microsoft.com/en-us/library/vstudio/bb548541(v=vs.110).aspx "MSDN: Enumerable.All<TSource> Method" 
[MSDN - Any()]: http://msdn.microsoft.com/en-us/library/bb337697.aspx "MSDN: Enumerable.Any<TSource> Method (IEnumerable<TSource>)"
[MSDN - Any(Func)]: http://msdn.microsoft.com/en-us/library/bb534972.aspx "MSDN: Enumerable.Any<TSource> Method (IEnumerable<TSource>, Func<TSource, Boolean>)"
[Stackoverflow-Count-Slower]: http://stackoverflow.com/a/11042691/1401257 "Stackoverflow: Which method performs better: .Any() vs .Count() > 0?"