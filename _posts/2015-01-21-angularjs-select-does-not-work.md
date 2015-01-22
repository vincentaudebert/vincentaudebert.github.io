---
layout: post
title: AngularJS select does not work
date:       2015-01-21 15:31:19
summary:    Your select does not work in AngularJS?
categories: angular javascript select
---

2015... Time to wish you happy new year guys!
And 2015 is crazy busy. So here comes the first post of the year and it's a really quick one.
Here is your problem: AngularJS select does not work. By does not work I mean is not populating the select box content. And of course, you get no errors in the console.
It occurred to me a few days ago and this answer is really easy.

Let's say you have this code.

{% highlight html %}
<select class="form-control" ng-options="book.id as book.title for book in books"></select>
{% endhighlight %}

This might generate a select box but with no options in it and the `form-control` class is not applied.

###How to fix it?
Do not go crazy. The answer is as easy as "funny".
You simply forgot the `ng-model` attribute.

Without this, select won't generate.

Here is the right code.
{% highlight html %}
<select class="form-control" ng-model="selectedBook" ng-options="book.id as book.title for book in books"></select>
{% endhighlight %}

Lesson learnt!

PS: Don't forget [to initialize selectedBook][1]

	[1]: http://vincentaudebert.github.io/angular/javascript/select/2014/11/11/angularjs-select-has-empty-value/