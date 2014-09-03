---
layout: post
title: Contact form with no server side
date:       2014-08-29 15:31:19
summary:    Build a contact form with no server side, only HTML (and Javascript if you want)
categories: html form
redirect_from: "/2014/08/29/angular-ui-bootstrap-tabset-activation-subtab.html"
---

While I was redesigning my personal website [vatweb.fr] [1], I really didn't want to have a server side involved just to send a basic contact form...

After a bit of Googling, I could not find anything better than [Wufoo] [2]... Not optimal but it would have done the job.

However, as you might have seen, I change my blog theme too to use [Pixyll jekyll theme] [3]. While I was looking inside the source code, I ended up finding [Brace.io] [4] in the `action` attribute of a form. Curious, I had a look and found out that Forms Brace.io allows you really easily to send a form content to your email address. Ideal for a contact form!

You can have a demo directly on this blog as it's using it for [the contact form] [5]

And here come the really easy HTML piece of code to build a Brace form:

{% highlight html %}
<form action="https://forms.brace.io/you@youremail.com" method="POST">
<input type="text" name="email" placeholder="Email Address">
<textarea type="text" name="content" rows="5" placeholder="What would you like to say?"></textarea>
<input type="submit" value="Say Hello">
</form>
{% endhighlight %}

Of course feel free to add some bootstrap classes and/or angularJS form validation :)

  [1]: http://vatweb.fr
  [2]: http://wufoo.com
  [3]: http://pixyll.com/
  [4]: http://forms.brace.io/
  [5]: http://vincentaudebert.github.io/contact.html
