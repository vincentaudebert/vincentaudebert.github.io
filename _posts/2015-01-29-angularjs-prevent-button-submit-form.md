---
layout: post
title: AngularJS How to prevent button to submit a form
date:       2015-01-21 15:31:19
summary:    A normal button submit your form when you just want it to trigger click event?
categories: angular javascript form
---

Another tiny good practice that we can easily forget.
Let's say you have a form with two buttons in it. You want that only one of them submit the form and you want the second to execute something on click but not to submit your form.

And you come with this code.

{% highlight html %}
<form ng-controller="YourController" ng-submit="Submit()">
	<button>Submit my form</button>
	<button ng-click="PrintSomethingAwesome()">Print Something Awesome</button>
</form>
{% endhighlight %}

As you can notice on [this JSFiddle][1] (open your console), both buttons are submitting the form. Concerning right?

###How to fix it?
Here comes the easy answer... and the "attribute jungle" of AngularJS :)

You simply need to add what type of button is your button. Legit.

Here is the right code.
{% highlight html %}
<form ng-controller="YourController" ng-submit="Submit()">
	<button type="submit">Submit my form</button>
	<button type="button" ng-click="PrintSomethingAwesome()">Print Something Awesome</button>
</form>
{% endhighlight %}

Working code on [this JSFiddle][2].

Solution inspired by [this useful post][3].

**N.B.: It's always cleaner/good practice to be clear in your HTML code and you should use `<input type="submit">` instead of a `<button type="submit">`**

  [1]: http://jsfiddle.net/vatweb/y85cytpq/
  [2]: http://jsfiddle.net/vatweb/mu4mhm59/
  [3]: https://github.com/angular/angular.js/issues/6017