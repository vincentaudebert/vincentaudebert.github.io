---
layout: post
title: OneAll - Polymer element
date:       2015-08-07 15:31:19
summary:    Connect to more than 30 social networks using this polymer element
categories: polymer element
---

Recently I was looking for a service that could provide a user authentication based on social networks.
I ended on [oneall.com] [1]

After having a look at the documentation I decided to build a polymer element for this service.

A month ago, I released v1.0 but this version did not include premium methods.
Here comes [v1.1] [2] that now supports all the methods provided by OneAll.

Feel free to participate to this repo.

To give you a preview, this is what you need to display this service on your website:
{% highlight html %}
<oneall-social-login>
  <a id="oneall-container">Login here</a> [if you use attachPopupUi]
  <div id="oneall-container">Login here</div> [if you use doRenderUi]
  [leave empty if you use doPopupUi]
</oneall-social-login>
{% endhighlight %}

You can find more examples in the `demo` folder on github.


  [1]: http://www.oneall.com
  [2]: https://github.com/vincentaudebert/polymer-oneall-social-login/tree/v1.1.0