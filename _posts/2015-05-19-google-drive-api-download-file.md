---
layout: post
title: Easy way to download a file using Google Drive API
date:       2015-05-19 15:31:19
summary:    Access token in the URL is the secret!
categories: google drive api download
---

While I was working with Google Drive API, I found a really useful trick.
Instead of having to add this annoying header to your get query `Authorization: Bearer [yourtoken]`, the easiest way is just to add your access token directly in your url as a parameter.

For instance if your URL is `https://docs.google.com/feeds/download/[yourfilekey]` just add `?access_token=[yourtoken]` at the end and then use this URL directly in your GET request.
It should download the file directly.

Article inspired by [this stackoverflow answer][1], EDIT #2.

  [1]: http://stackoverflow.com/a/18927228/4143960