---
layout: post
title: React PropTypes - errors and good practice
date:       2017-03-21 10:31:19
summary:    What errors you can get and what I recommend you to do...
categories: javascript react proptypes
---

React PropTypes are a very cool tool to help you to debug/develop your React app.

Let's go through some errors you can get.

### The errors

First the errors are actually just warnings in your browser console.

They will only show up in development mode. Not in production.

```
Warning: Failed prop type: Invalid prop `handleSubmit` of type `string` supplied to `YourComponent`, expected `function`.
```

This warning means that you are expecting `YourComponent` property `handleSubmit` to be a function but it actually receives a string.

These warnings are really helpful to help you to debug your React application.

### Best practices

First, of course, you should define `PropTypes` for all your components.

Go to as much details as you can. For instance, define what object properties should be too.

Many React tutorials you will find online will show `PropTypes` defined at the end of the file. I don't really agree with this. I always define my proptypes at the top of the file in their own variable. So when I open the file I know directly what this component is expecting. Saving me some painful scrolling.

```
import React, { PropTypes } from 'react';

const propTypes = {
    name: PropTypes.string.isRequired,
};

const YourComponent = ({ name }) => {
    return (
        <div>Name: {name}</div>
    )
};

YourComponent.propTypes = propTypes;

export default YourComponent;
```

Also if your property is not required you should define a default value using `defaultProps`.

```
import React, { PropTypes } from 'react';

const propTypes = {
    name: PropTypes.string,
};

const defaultProps = {
    name: 'Your name',
};

const YourComponent = ({ name }) => {
    return (
        <div>Name: {name}</div>
    )
}

YourComponent.propTypes = propTypes;
YourComponent.defaultProps = defaultProps;

export default YourComponent;
```

I highly recommend that you make `PropTypes` required in your linting tools.

They are by default if you use [`create-react-app`] [2] or AirBnb eslint config.

You can get more information on [`PropTypes` here] [1]

  [1]: https://facebook.github.io/react/docs/typechecking-with-proptypes.html
  [2]: https://github.com/facebookincubator/create-react-app