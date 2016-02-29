---
layout:     post
title: Iframe & Windows 8.1 metro app
date:       2014-07-16 15:31:19
summary:    Manage iframes in a Windows 8.1 metro app
categories: windows app
redirect_from: "/2014/07/16/iframe-windows-8-1-metro-app.html"
redirect_from: "/windows/app/2014/07/17/iframe-windows-8-1-metro-app/"
---

Let’s start this blog with the problem which gave me the idea of starting it.

I’m a web developer currently working for a startup called [Showcase Workshop][1]. While I was programming for our Windows 8 app I faced a problem when I needed to integrate HTML page in an iframe.

Basically, I had a HTML page coming for my local cache (`ms-appdata`) and I could not load it in an `iframe` using something like this:

`<iframe src=”ms-appdata:///local/index.html”></iframe>`

I was getting a blank iframe. Then I tried with a web context iframe:

`<iframe src=”ms-appx-web:///local/index.html”></iframe>`

Unfortunately, `ms-appx-web` can’t access to a local resource but only to resources in the app package. So I was getting a black iframe…

After a bit of googling I found this page: [http://blogs.windows.com/windows/b/appbuilder/archive/2013/07/17/what-s-new-in-webview-in-windows-8-1.aspx][2]

Finally, I made it work with:

`<x-ms-webview src=”ms-appdata:///local/index.html”></x-ms-webview>`

You can find `x-ms-webview` documentation here: [http://msdn.microsoft.com/en-us/library/windows/apps/dn301831.aspx][3]

N.B.: You might want to add this tag directly with jQuery but then you will get the famous security exception:

> 0x800c001c — JavaScript runtime error:
> Unable to add dynamic content. A
> script attempted to inject dynamic
> content, or elements previously
> modified dynamically, that might be
> unsafe. For example, using the
> innerHTML property to add script or
> malformed HTML will generate this
> exception. Use the toStaticHTML method
> to filter dynamic content, or
> explicitly create elements and
> attributes with a method such as
> createElement. For more information,
> see
> [http://go.microsoft.com/fwlink/?LinkID=247104][4].

I recommend to put `x-ms-webview` in hard in your HTML code with `display:none;` and then dynamically set the right `src` and display it when needed.


  [1]: http://www.showcaseworkshop.com
  [2]: http://blogs.windows.com/windows/b/appbuilder/archive/2013/07/17/what-s-new-in-webview-in-windows-8-1.aspx
  [3]: http://msdn.microsoft.com/en-us/library/windows/apps/dn301831.aspx
  [4]: http://go.microsoft.com/fwlink/?LinkID=247104
