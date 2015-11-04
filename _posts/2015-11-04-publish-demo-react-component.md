---
layout: post
title: Publish demo of your React component on GitHub
date:       2015-11-04 15:31:19
summary:    Made super easy by rackt-cli
categories: javascript react
---

Just started at my new job! Exciting!

And my first mission was to deal with this [React component] [1]
We wanted to have a nice demo page on a github page for this component.

Something [like this] [2]...

And it was actually fairly easy. Using [rackt-cli] [3]

Once rackt-cli is installed (using `npm install -g rackt-cli`), create a folder `examples` and then everything inside this folder will be taken to a github page for your project using the command `rackt pages`

Easy right?

In my case, I copied a github page theme (index.html + javascripts folder + stylesheets folder) and then modified the index to list my different demos (basic folder + multiple folder). You can see the structure [here] [4]

N.B.: rackt-cli can also be used to `build` your react component and you can preview your demo using `rackt server` and... much more! Just check [the documentation] [3]

  [1]: https://github.com/springload/react-svg-icon
  [2]: https://springload.github.io/react-svg-icon/
  [3]: https://github.com/mzabriskie/rackt-cli
  [4]: https://github.com/springload/react-svg-icon/tree/master/examples