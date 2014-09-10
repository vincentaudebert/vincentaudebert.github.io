---
layout: post
title: How to test properly a string var in Javascript?
date:       2014-09-10 15:31:19
summary:    Reminder how to test properly a string var in Javascript
categories: javascript string
---

Sometimes it's good to remind the basis.

Today, I was trying to test if a `Date` object that I made becoming a string using `toISOString()` was a string.

And I immediately thought about `if(date instanceof String)` but this was always `false`...

And then I found this post: [http://stackoverflow.com/a/21605936] [1]

It was painful to see how sometimes you forget that Javascript can be crap and you need a basic reminder.

I created **[a little JSFiddle] [2]** to show exactly what I wanted to do and to make obvious the difference between literals and objects.
But you can also see the code just here:

{% highlight javascript %}
var date = new Date();
var dateStr = date.toISOString();

console.log(dateStr instanceof String); //false
console.log(typeof dateStr === "string"); //true

var dateStrObj = new String(dateStr);

console.log(dateStrObj instanceof String); //true
console.log(typeof dateStrObj === "string"); //false

//Recommendation
//For more security keep testing the two ways
console.log(dateStr instanceof String || typeof dateStr === "string"); //true
console.log(dateStrObj instanceof String || typeof dateStrObj === "string"); //true
{% endhighlight %}

Finally, another link you might find useful on the Literals Vs Objects topic: [http://stackoverflow.com/questions/203739/why-does-instanceof-return-false-for-some-literals] [3]

  [1]: http://stackoverflow.com/a/21605936
  [2]: http://jsfiddle.net/vatweb/Lcw7fz88/
  [3]: http://stackoverflow.com/questions/203739/why-does-instanceof-return-false-for-some-literals
