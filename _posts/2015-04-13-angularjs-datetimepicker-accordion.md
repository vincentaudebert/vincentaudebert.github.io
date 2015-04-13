---
layout: post
title: AngularJS Datetime picker inside an accordion not working/displayed
date:       2015-04-13 15:31:19
summary:    How to modify a value stored in parent scope from a child?
categories: angular javascript scope
---

A quick post about a "funny" bug I faced yesterday.
I had an `input` as datepicker (using Angular UI) in a list of filter on the left side of my page.
And then specifications changed and I had to put this date filter inside a collapsable `div`.

I chose to use `<accordion>` still from Angular UI.

##First problem
First problem was that once the datepicker was inside the accordion, it was not opening.
It was an easy fix as accordion creates a child scope. So you need to put your opening vars inside a wrapper.

##Second problem
Second problem which was a bit more tricky was that my datepicker wasn't displayed properly and was limited to the accordion borders.
Here comes the attribute `datepicker-append-to-body="true"` to add to your datepicker `input`.
Then everything should be fine, working and well displayed!

Found the solution to my second problem by using this [stackoverflow answer][1].

  [1]: http://stackoverflow.com/questions/19572074/angularjs-datepicker-not-displaying-totally-on-bootstrap-3-collapse-accordion