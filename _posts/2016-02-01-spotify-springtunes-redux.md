---
layout: post
title: Control your Spotify client with your browser
date:       2016-02-01 15:31:19
summary:    When playing with Redux leads to a cool little npm package
categories: javascript react
redirect_from: "/javascript/react/2016/02/01/spotify-springtunes-redux-copy/"
---

The beginning of the year is generally light here in New Zealand. You know... the time everybody gets back to work :)

So I got the chance to explore [Redux] [1]... and I learnt A LOT! What a really cool way to manage the state of your React app.

### Get started

First if like me you are not used to Flux and even less to Redux, you should check these [cool tutorial videos] [2] made by the creator of Redux. It will give you some really useful basics and help you to understand how Redux works.

### Starter kit

Then, it's time to get started and write some code.

And here come the [examples] [3] from Redux git repo. Clearly, they are really amazing and you can totally use them as a base for your first small project in Redux.

### Springtunes

![Springtunes screenshot](https://github.com/springload/springtunes/raw/master/screenshots/sc_springtunes.png?raw=true "Springtunes screenshot")

That's what I did and I ended up creating [Springtunes] [4]. A small web app that allows you to control your spotify client from any web browser.

It's running an express server on port 3000 and then through the UI, triggers actions to the actual Spotify client.

All the client side is made using React and Redux. Don't hesitate to have a look at the source code but it's mostly based on the 'async' example from Redux repo.

### Afterwards

That's the crazy thing... Everything is so clear and well explained in the [videos] [2]/[examples] [3]/[documentation] [1] that you don't need anything else to get started and nail Redux.

Enjoy Redux, it looks complex at the beginning but it's a lot of fun at the end :)

  [1]: http://redux.js.org/
  [2]: https://egghead.io/series/getting-started-with-redux
  [3]: https://github.com/rackt/redux/tree/master/examples
  [4]: https://www.npmjs.com/package/springtunes
