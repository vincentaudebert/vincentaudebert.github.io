---
layout: post_page
title: Angular UI Bootstrap Tabset and subtabs
---

Few problems solved in this post. 

After a long investigation I found quite not clear and not documented how to use Angular UI Bootstrap tabsets.
I was basically trying to have a range of tabs/subtabs and just activating them using `active` attribute.



### First issue
More precisely, this issue: [https://github.com/angular-ui/bootstrap/issues/611][1]

According to this github issue, it's not possible to use any expression/function evaluation in `active` attribute. You have to use a boolean var.

That's the reason why I created an array to manage each tabs.



### Second problem
How to activate parent tabs when clicking on a child tab?

To manage this I use the function `includes()` ([Documentation] [4]) of `$state` and I use dot-separated names for my routes like "foo.bar". Thanks to this I can look for "foo" to activate the parent tab and "foo.bar" for the child tab.

**You will find a basic 3-level tab example on this JSFiddle: [http://jsfiddle.net/vatweb/g1Lem3Lw/] [2]**

Here is another link I used to give me an idea about expression evaluation in `active`: [http://plnkr.co/edit/F57uuiiqAbQ92QWfkYp8?p=preview] [3]

  [1]: https://github.com/angular-ui/bootstrap/issues/611
  [2]: http://jsfiddle.net/vatweb/g1Lem3Lw/
  [3]: http://plnkr.co/edit/F57uuiiqAbQ92QWfkYp8?p=preview
  [4]: https://github.com/angular-ui/ui-router/wiki/Quick-Reference#stateincludesstatename--params
