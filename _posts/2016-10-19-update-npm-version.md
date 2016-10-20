---
layout: post
title: Update a NPM package version
date:       2016-10-19 10:31:19
summary:    And keep your GIT repo consistent
categories: javascript npm
---

Back from holidays and very little time to write a post!

Let's have a quick look at updating a NPM package version in a clean and easy way. Well, it's not that hard anyway.

## Prerequisites

- In your `package.json` make sure you have a `prepublish` command that will be run when you do the final `npm run publish`. Usually this command runs a build of the package in production mode.

- I'll consider you are already hooked up with NPM website. If not see: [https://docs.npmjs.com/getting-started/publishing-npm-packages#creating-a-user] [1]

- I will also consider that all the package information about your package are present into `package.json`. They should be if it's a version update anyway :)

## Let's update!

- Open your terminal and go to your package root folder.

- Make your changes on code base and commit your changes.

- Once you are sure everything is fine, `npm version patch` (will bump third number, i.e. 0.1.5 -> 0.1.6) or any other more appropriate argument (see [https://docs.npmjs.com/cli/version] [2])

- Run `git push origin master --tags`. 
`npm version` also creates a tag. So we need to push the tags in order to have the version available in Github too.

- Run `npm publish`

- Check your package on [http://www.npmjs.com] [3] it should have been updated!

**PS:** You are more than a thousand to visit my blog/articles every months. Thanks a lot! This is super motivating and hope it helps you :)

  [1]: https://docs.npmjs.com/getting-started/publishing-npm-packages#creating-a-user
  [2]: https://docs.npmjs.com/cli/version
  [3]: http://www.npmjs.com
