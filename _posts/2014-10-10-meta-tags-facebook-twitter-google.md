---
layout: post
title: Meta tags for Facebook, Twitter and Google+
date:       2014-10-10 15:31:19
summary:    Sharing can be love... but must be accurate!
categories: html meta share
---

A really quick post about meta tags and a nice way to make your page sharing more accurate/attractive on Facebook, Twitter, Google+ and all the main other social networks.

I think the first one to start with specific header meta tags was Facebook. With their own "bot" called OpenGraph, they scan websites and target first specific meta tags in your `head` tag. If you don't have these tags, they might fall back to your default ones but I saw many times this system failing and/or putting something broken/not relevant in place of your actual page title or description. So it's probably better to just add them to your page just to be sure your saving is safe.

###Facebook
Let's have a look to Facebook specific meta tags.

{% highlight html %}
<meta property="og:title" content="Title Here" />
<meta property="og:type" content="article" />
<meta property="og:url" content="http://www.example.com/" />
<meta property="og:image" content="http://example.com/image.jpg" />
<meta property="og:description" content="Description Here" />
<meta property="og:site_name" content="Site Name, i.e. Moz" />
<meta property="article:published_time" content="2013-09-17T05:59:00+01:00" />
<meta property="article:modified_time" content="2013-09-16T19:08:47+01:00" />
<meta property="article:section" content="Article Section" />
<meta property="article:tag" content="Article Tag" />
<meta property="fb:admins" content="Facebook numberic ID" /> 
{% endhighlight %}

I think everything is pretty clear and well named.
I've applied this example for this blog (as you can see in the source):

{% highlight html %}
<meta property="og:title" content="VatWeb <CODE> Blog"/>
<meta property="og:type" content="blog"/>
<meta property="og:url" content="http://vincentaudebert.github.io/"/>
<meta property="og:image" content="/ico/apple-touch-icon-144-precomposed.png"/>
<meta property="og:description" content="You can keep liking lolcat pictures... or you can check out VatWeb coding blog and learn something new"/>
{% endhighlight %}

You will see it if you share my page on Facebook. I found much more fun to put a specific Facebook related message as a description instead of just my page description.

###Twitter
And now Twitter specific meta tags, called "Twitter card".

{% highlight html %}
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@publisher_handle">
<meta name="twitter:title" content="Page Title">
<meta name="twitter:description" content="Page description less than 200 characters">
<meta name="twitter:creator" content="@author_handle">
<!-- Twitter summary card with large image must be at least 280x150px -->
<meta name="twitter:image:src" content="http://www.example.com/image.html"> 
{% endhighlight %}

I've applied this example for this blog (as you can see in the source):

{% highlight html %}
<meta name="twitter:card" content="summary">
<meta name="twitter:url" content="http://vincentaudebert.github.io/">
<meta name="twitter:title" content="VatWeb <CODE> Blog">
<meta name="twitter:description" content="You can retweet Justin Bieber... or you can check out VatWeb coding blog and learn something new">
<meta name="twitter:image" content="/ico/apple-touch-icon-144-precomposed.png">
<meta name="twitter:creator" content="@vatweb">
{% endhighlight %}

Same than for Facebook, I chose to put a Twitter related message as a description.

###Google+

{% highlight html %}
 <!-- Google Authorship and Publisher Markup -->
<link rel="author" href="https://plus.google.com/[Google+_Profile]/posts"/>
<link rel="publisher" href=”https://plus.google.com/[Google+_Page_Profile]"/>

<!-- Schema.org markup for Google+ -->
<meta itemprop="name" content="The Name or Title Here">
<meta itemprop="description" content="This is the page description">
<meta itemprop="image" content="http://www.example.com/image.jpg"> 
{% endhighlight %}

For Google+, I chose to reuse my Facebook description, and I don't have a Google+ profile, so I don't specify any profile which gives:

{% highlight html %}
<meta itemprop="name" content="VatWeb <CODE> Blog">
<meta itemprop="description" content="You can keep liking lolcat pictures... or you can check out VatWeb coding blog and learn something new">
<meta itemprop="image" content="/ico/apple-touch-icon-144-precomposed.png"> 
{% endhighlight %}

###LinkedIn

So far from what I know, LinkedIn is using the same tags than Facebook.

###Sources

This page is based using [this blog post] [1] and [this other page] [2].

  [1]: http://moz.com/blog/meta-data-templates-123
  [2]: http://www.iacquire.com/blog/18-meta-tags-every-webpage-should-have-in-2013
