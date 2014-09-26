---
layout: post
title: MEAN.io... yes it s mean!
date:       2014-09-26 15:31:19
summary:    Incredible project starter using mongodb, express.js, angularjs and node.js
categories: frameworks node angular nosql
---

Busy busy busy!

For the last few weeks, I've been really busy between my job and a personnal project.

This personnal project was really interesting as I discovered a awesome new project starter called **MEAN.io**

MEAN stands for MongoDB Express.js AngularJS Node.js

From these technologies I knew only AngularJS and what I can say is that it's amazingly powerful! I would say MEAN represents a really easy and quick way to start and realize a small project. As it's based on MongoDB, the NoSQL database might be too limited for really big projects but I would highly recommend it for small presentation websites or easy CRUD data management.

To get started quickly, first have a look at the official website: [http://mean.io] [1]

You will need npm, Grunt, Bower and all these packages you should already have installed anyway if you are an angular user.

And then let's get your mind blowed away:

First to setup all your app, execute this in your terminal:

{% highlight code %}
> sudo npm install -g meanio@latest  // Get the mean cmdline
> mean init myApp                    // create your first app
> cd myApp && npm install            // Install dependencies
> grunt                              // Launch mean
{% endhighlight %}

Note that you can also run `node server` instead of `grunt`.

After this have a look to the [documentation] [2] and explore the folder called "articles" inside your "packages" one. It will give you an idea of a basic CRUD system. And then yes... it's as easy as this!
I would say that the most complicated thing I faced on my small project was probably to use/get foreign keys with mongoose but that really well documented [here] [3].

### Bonus point
Big bonus point for mean is that you can easily deploy your app on [Heroku] [4]
Behind its complicated terms, Heroku is a powerful web host and you will be able to deploy your app online by using this magic command line: `git push heroku master`

**Yes, it's everything as easy as this!** 

  [1]: http://mean.io
  [2]: http://mean.io/#!/docs
  [3]: http://mongoosejs.com/docs/populate.html
  [4]: http://heroku.com
