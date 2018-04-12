---
layout: post
title: When & Why use unstated
date:       2018-04-12 10:31:19
summary:    Rather than using the traditional Redux or MobX
categories: javascript react state
---

I had some interesting time on [`react-accessible-accordion` package][1].

At Springload, we got excited by React 16.3 and its [Context API][2]. I read some articles and I found out this nice package called [`unstated`][3].

I want to talk about it because it helped us to reduce our package size by _81%_ compared to the version using `MobX`.

### When to use it?

`unstated` is a nice and small state manager.

You usually want to use one of these when you face `props drilling`. It is that case where you pass properties down many levels to many components.

If you think you need `Redux` or `MobX` then you might want to investigate the use of `unstated`.

### Why use it?

Well, the first argument is a no brainer: the size.

#### The size

Let's compare `Redux`, `MobX` and `unstated` packages (using the very useful package [`package-size`][4]):

##### Redux:

Including `redux` and `react-redux`:

* Minified: 20.64 KB
* GZipped: 6.63 KB

##### MobX

Including `mobx` and `mobx-react`:

* Minified: 63.7 KB
* GZipped: 19.7 KB

##### Unstated

Note that we don't need many packages here:

* Minified: 4.85 KB
* GZipped: 1.46 KB

In both versions `unstated` is about **77%** lighter than `Redux` and **92%**(!) lighter than `MobX`.

As I said before: no brainer. Luckily, its small size also brings simplicity.

#### The simplicity

`Redux` and `MobX` allow you to achieve a lot. You dispatch actions to update many stores, you can even deal nicely with API calls using `redux-saga` for instance.

For complex apps, these have a really big advantage on `unstated` and, for now, you should definitely use them instead of `unstated`.

But for instance, if you simply care about having an app state and be able to access it and change it depending on some user actions across your app. Then `unstated` is a serious candidate.

For me the most convincing argument was its simplicity verbose wise.

With `unstated` you just have to deal with a container and a component which subscribe to it.

What is achieved with many different files on `Redux` can fit in a single file on `unstated` if you want. And it makes sense. The main idea behind `unstated` is to keep the easiness of `setState` from a React component.

You have your state, you want to change it, you call a function from your container, it's triggering `setState` and the new state is spread across your app. Easy.

No action, no constant, no reducer, none of that.

For those who like pieces of code as examples, the README from the original repo as a good [guide section][5].

#### BONUS: The backward compatibility

`unstated` is based on the new Context API from React 16.3

The good news is that it includes a polyfill for this API which allows you to use `unstated` on previous React versions.

---

I hope this will convince you to give a try to `unstated` when you don't need the extra complexity of `Redux` or `MobX`. It's a good way to speed up your productivity and have a lighter app.

Check `unstated` on [GitHub][3] or on [npm][6].

[1]: https://github.com/springload/react-accessible-accordion/
[2]: https://medium.com/dailyjs/reacts-%EF%B8%8F-new-context-api-70c9fe01596b
[3]: https://github.com/jamiebuilds/unstated
[4]: https://www.npmjs.com/package/package-size
[5]: https://github.com/jamiebuilds/unstated#guide
[6]: https://www.npmjs.com/package/unstated
