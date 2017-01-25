---
layout: post
title: Sourcemaps configuration with Webpack
date:       2017-01-25 10:31:19
summary:    Let's optimise your development config a bit...
categories: javascript webpack config
---

First post of 2017! Happy new year everyone!

Let's talk about [Webpack] [1] (still the version 1... ;)).

Yeah I know. That sounds scary. Especially when you dive into the config hell it can be.

Recently, I faced an issue. I tried to optimise my build in development by using the `devtool` called `cheap-module-eval-source-map`.

I got some amazing improvements in my build time compared to the one I was using before: `inline-source-map`. 20 seconds instead of 28 seconds...

### Problem... Debug has become totally messed up...

Then I started developing and at some point I raised an exception.

And wow! My debug console wasn't telling me the filename nor the faulty line!

Instead I was getting something like `?d41d:17`... And when I was clicking on it...

```
undefined


// WEBPACK FOOTER //
// 
```

Ok thanks Webpack/Chrome/Whatever-is-responsible-for-that!

### The solution...

Turned out Webpack is guilty.

I found this very useful [github issue] [2].

And I applied some of the suggestions. The one which worked for me was [this one] [3].

```
config.plugins.push(new webpack.SourceMapDevToolPlugin({
    filename: '[file].map',
    columns: false,
}));
```

The `columns: false` is important and will make the build as fast as `cheap-module-eval-source-map`.

You also need to delete/comment the `config.devtool = ` line if you have any.

Your faulty file and line should show up again in your browser and the build should still be pretty fast.

For more information about the different devtools, [check the documentation here] [4]

  [1]: https://webpack.github.io/
  [2]: https://github.com/webpack/webpack/issues/2145
  [3]: https://github.com/webpack/webpack/issues/2145#issuecomment-251691937
  [4]: https://webpack.github.io/docs/configuration.html#devtool