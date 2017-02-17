---
layout: post
title: How to import / export in React/ES6?
date:       2016-05-15 10:31:19
summary:    To default or not to default...
categories: javascript react es6
---

Quick note that might help some of you.

## How to import / export classes (especially components) in React/ES6?

### The errors

If you get distracted you might end up exporting or importing your classes the wrong way.
And getting one of these errors:

```
Uncaught Invariant Violation: Element type is invalid: expected a string (for built-in components) or a class/function (for composite components) but got: undefined. Check the render method of `YourComponent`.
```

or 

```
Uncaught TypeError: Super expression must either be null or a function, not undefined
```

### One possibility: default

If you have a closer look at your class `YourComponent`, you probably defined it like this:

{% highlight javascript %}
export class YourComponent extends React.Component
{% endhighlight %}

And then tried to import it in another file like this:

{% highlight javascript %}
import YourComponent from './YourComponent'
{% endhighlight %}

For this particular case, `YourComponent` should be declared as `default`, like this:

{% highlight javascript %}
export default class YourComponent extends React.Component
{% endhighlight %}

And then your import will work.

### Other possibility: no default

Now let's say your module `YourComponent.js` contains more than one class/var and you don't really want to default any of them.

You will keep declaring `YourComponent` like this:

{% highlight javascript %}
export class YourComponent extends React.Component
{% endhighlight %}

And change your import to use curly braces, like this:

{% highlight javascript %}
import { YourComponent } from './YourComponent'
{% endhighlight %}

**N.B.: The Airbnb styleguide disallows having multiple class components in the same file. But you can use [stateless components] [3].**

### More examples

You will find more examples at these addresses:

- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import] [1]
- [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export] [2]



  [1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import
  [2]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export
  [3]: https://hackernoon.com/react-stateless-functional-components-nine-wins-you-might-have-overlooked-997b0d933dbc#.i40s0jpc3
