---
layout: post
title: AngularJS $http error callback not executed
date:       2015-09-03 15:31:19
summary:    You probably need to intercept better
categories: angularjs http callback
---

Just found a solution to my problem and thought it would be a good idea to share it.
Few days ago we changed our structure and we are now using factories to call our API.

Unfortunately, we realized that since we made this change our `error` callbacks were not executed anymore.

I first thought the problem was linked somehow to the server return as we changed the way we handle exceptions. But it was not.

The real weird thing was that we were always going into the `success` callback and never into the `error` one even with an error 500 or 404 or whatever...

So I googled it (quite a lot) and then found this brilliant [stackoverflow answer] [1] which gives the right answer (for me) on the second answer.

Here was my problem. I was intercepting the errors like this:
{% highlight javascript %}
return {
$httpProvider.interceptors.push(function ($timeout, $q, $injector) {
...
	responseError: function (rejection) {
		if (rejection.status === 403) {
			growl.error('Access denied');
			return rejection;
		}

		if (rejection.status !== 401) {
			return rejection;
		}
	}
...
{% endhighlight %}

But as it says on SO answer it should have been:
{% highlight javascript %}
return {
$httpProvider.interceptors.push(function ($timeout, $q, $injector) {
...
	responseError: function (rejection) {
		if (rejection.status === 403) {
			growl.error('Access denied');
			return $q.reject(rejection);
		}

		if (rejection.status !== 401) {
			return $q.reject(rejection);
		}
	}
...
{% endhighlight %}

Indeed in case of rejection you need to return it otherwise Angular thinks that everything is fine and go through the `success` callback!

Hope this helps!

  [1]: http://stackoverflow.com/questions/15888162/angularjs-http-error-function-never-called