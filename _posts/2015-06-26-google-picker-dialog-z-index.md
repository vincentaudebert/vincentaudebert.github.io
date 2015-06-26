---
layout: post
title: Google Picker dialog behind bootstrap modal
date:       2015-06-26 15:31:19
summary:    z-index is your friend!
categories: google picker dialog css 
---

Another article talking about Google API and it's awesome Google Picker which allows you to pick files from your Google Drive.

I tried to display it on top of a modal on my screen and I could not see the Google Picker dialog showing up.
It was simply hidden behind the modal.

And here comes `z-index`.

Using jQuery, the best solution is to change on the fly `z-index` property for class `.picker-dialog`.
Use a `z-index` > 1050 or the value of your modal one.

Here is the code I use.
{% highlight javascript %}
$('.picker-dialog').css('z-index', 5000);
{% endhighlight %}

Hope this helps!

Article inspired by [this github issue][1].

  [1]: https://github.com/softmonkeyjapan/angular-google-picker/issues/4