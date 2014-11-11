---
layout: post
title: AngularJS select has empty value
date:       2014-11-11 15:31:19
summary:    Figure out why sometimes AngularJS adds a "?"/empty value into select elements
categories: angular js select
---

A quick post to understand why AngularJS adds a empty value at the beginning of your select box.

Let's say you have this code.

{% highlight html %}
<select class="form-control" ng-model="selectedBook" ng-options="book.id as book.title for book in books"></select>
{% endhighlight %}

This might generate something like:

{% highlight html %}
<select id="item-track" ng-model="selectedBook" ng-options="book.id as book.title for book in books">
	<option value="?" selected="selected"></option>
	<option value="0">Title Book #1</option>
	<option value="1">Title Book #2</option>
	<option value="2">Title Book #3</option>
</select>
{% endhighlight %}

Why do you get an option with a value `?` and no text inside?

It's because your model `selectedBook` isn't initialized with a value. In order to not select a default actual value, AngularJS generates a empty option and selects it by default.

###How to fix it?

{% highlight html %}
<select class="form-control" ng-model="selectedBook" ng-options="book.id as book.title for book in books" ng-init="selectedBook=0"></select>
{% endhighlight %}

In this code we specify a initial value for `selectedBook`. It will generates this:

{% highlight html %}
<select id="item-track" ng-model="selectedBook" ng-options="book.id as book.title for book in books" ng-init="selectedBook=0">
	<option value="0" selected="selected">Title Book #1</option>
	<option value="1">Title Book #2</option>
	<option value="2">Title Book #3</option>
</select>
{% endhighlight %}

Note that `ng-init` allows functions. So you could call a function `initSelect()` which could wait for another value to initialize `selectedBook` or whatever :)

You can find a JSFiddle for this article [here][1]
And this article is inspired by this [stackoverflow answer][2]

  [1]: http://jsfiddle.net/vatweb/e8d6s68a/
  [2]: http://stackoverflow.com/a/13809295/4143960
