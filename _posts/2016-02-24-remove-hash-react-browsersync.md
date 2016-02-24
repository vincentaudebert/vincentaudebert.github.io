---
layout: post
title: Remove hash in a React App served by BrowserSync
date:       2016-02-24 15:31:19
summary:    A couple of special tricks
categories: javascript react
---

You probably noticed that by default react app navigation is using the famous `/#/` in the url.

But what if you want to have "proper" urls like `domain.com/foo/bar` instead of `domain.com/#/foo/bar`?

### The React part

Inside your [React] [3] app you will need to make a simple change.
Change the `history` argument for your `<Router>` from `hashHistory` to `browserHistory`

```
import { Router, browserHistory } from 'react-router';

ReactDOM.render ((
 <Router history={browserHistory} />
   ...
 </Router>
), document.body);
```

### The BrowserSync part

Now the other part is to make your [BrowserSync] [4] server (gulp task here) able to serve these urls.
To do so, just add some middleware in your config:

```
const historyApiFallback = require('connect-history-api-fallback');

...

gulp.task('browser-sync', function() {
    browserSync({
        server: {
            baseDir: './',
            middleware: [historyApiFallback()]
        },
        notify: false
    });
});
```

And then you should be able to access to `domain.com/foo/bar`

This post is based on 2 stackoverflow posts:
- [One to remove the hash part] [1]
- [The other one to configure BrowserSync] [2]

  [1]: http://stackoverflow.com/a/33108975/2462089
  [2]: http://stackoverflow.com/a/33798349/2462089
  [3]: https://facebook.github.io/react/
  [4]: https://www.browsersync.io/
