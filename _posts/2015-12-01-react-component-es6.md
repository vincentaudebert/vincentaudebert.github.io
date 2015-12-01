---
layout: post
title: How to create a React component with ES6
date:       2015-12-01 15:31:19
summary:    Few tips to create your component with ES6
categories: javascript react
---

Let's keep going with ReactJS. Must say I'm getting addicted :)

Recently I started a small project and I wanted to use ReactJS and ES6 ([EcmaScript 2015 6th Edition] [1])

Turned out that creating a component is a little bit different.
Let me show you a commented skeleton for a component in ES6:

{% highlight javascript %}
//Your component inherits from React.Component
export class Counter extends React.Component {
  //In ES6, getInitialState() is gone
  //You need to use the constructor and init your property 'state' inside
  constructor(props) {
    super(props);
    this.state = {count: props.initialCount};
  }
  tick() {
    this.setState({count: this.state.count + 1});
  }
  render() {
    return (
      <div onClick={this.tick.bind(this)}>
        Clicks: {this.state.count}
      </div>
    );
  }
}
//propTypes and defaultProps are now declared as properties on the constructor instead of directly inside the class body.

//This is how you declare the props for your component
Counter.propTypes = { initialCount: React.PropTypes.number };
//And how you give them a default value
Counter.defaultProps = { initialCount: 0 };
{% endhighlight %}

This example comes directly [from the official ReactJS documentation][2] that I highly recommend.

  [1]: http://www.ecma-international.org/ecma-262/6.0/
  [2]: https://facebook.github.io/react/docs/reusable-components.html#es6-classes