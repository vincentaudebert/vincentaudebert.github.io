---
layout: post
title: AngularJS Scope propagation from child to parent
date:       2015-02-27 15:31:19
summary:    How to modify a value stored in parent scope from a child?
categories: angular javascript scope
---

Recently, I had a bit of trouble to propagate my changes form a child scope to my parent scope var.
Let's say you have a parent scope with a var `displayMessage` you want to display a different message once you have loaded your child controller.

Basically, if you leave this var directly attached to scope, you will be able to access it in your child scope but any modification will not be propagated to your parent scope. Modification will stay in child scope.

To fix this issue, you need to wrap this var in a container object. Let's named it `container` and you now have `container.displayMessage`. Any modification made on this object in the child will be propagated to the parent scope.

It's quite hard to explain by text but everything should be clearer with this [this JSFiddle][1].

This post has been inspired by this [stackoverflow answer][2].

  [1]: http://jsfiddle.net/vatweb/06wub973/1/
  [2]: http://stackoverflow.com/a/16973319/4143960