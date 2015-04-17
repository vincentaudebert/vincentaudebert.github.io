---
layout: post
title: The most forgotten HTML tag for a table... <caption>
date:       2015-04-13 15:31:19
summary:    When you want to add a "title" to your table
categories: html tag caption
---

The other day, I was creating a `<table>` and I wanted to add a title at the top of it.
Usually, and I think like most of the people, I would use a `<h2>` or something similar to make a clear separation with the rest of my code.

And then I found this amazing forgotten tag... `<caption>`

If you add it inside your `<table>` you will have a lovely title for your table and will be able to customize it as much as you want.

You can have a look to [this simple example on JS Fiddle] [1].

Or you can have an idea with this piece of code:
{% highlight html %}
 <table style="width:400px">
     <caption style="font-weight:bold; font-size:30px; color:green;">ZOMG a table title!</caption>
 <thead>
  <tr>
     <th>Month</th>
     <th>Savings</th>
  </tr>
 </thead>
 <tfoot>
  <tr>
     <td>Sum</td>
     <td>$180</td>
  </tr>
 </tfoot>
 <tbody>
  <tr>
     <td>January</td>
     <td>$100</td>
  </tr>
  <tr>
     <td>February</td>
     <td>$80</td>
  </tr>
 </tbody>
</table> 
{% endhighlight %}

  [1]: http://jsfiddle.net/vatweb/q4zk5pdn/