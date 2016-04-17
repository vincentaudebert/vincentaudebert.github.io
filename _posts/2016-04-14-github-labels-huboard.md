---
layout: post
title: GitHub label management to use with Huboard
date:       2016-04-14 10:31:19
summary:    Copy/create labels into a new repository
categories: project management
---

Recently at [Springload] [1], we are exploring the idea of using [Huboard] [2] to have a better view on our workload on a project and use the full potential of [GitHub] [3].

Most of it, I believe, comes from a good utilisation of the labels.

On this page, I will take you through the process I used to copy/create new labels in order to have a nice structure ready for [Huboard][2].

### The main tool

We are going to use `github-label-sync` which is a really cool NPM package [available here] [4] or even simpler, using `npm install -g github-label-sync`.

### The process

#### Get the config

In my case, I used an existing repository where I had some cool labels I wanted to reuse but I also needed to add new ones.

I recommend using the GitHub interface to create your extra labels and then run [this script] [5]

{% highlight javascript %}
// go on you labels pages
// eg https://github.com/cssnext/cssnext/labels
// paste this script in your console
// copy the output and now you can import it using https://github.com/popomore/github-labels !

var labels = [];
[].slice.call(document.querySelectorAll(".label-link"))
.forEach(function(element) {
  labels.push({
    name: element.textContent.trim(),
    // using style.backgroundColor might returns "rgb(...)"
    color: element.getAttribute("style")
      .replace("background-color:", "")
      .replace(/color:.*/,"")
      .trim()
      // github wants hex code only without # or ;
      .replace(/^#/, "")
      .replace(/;$/, "")
      .trim(),
  })
})
console.log(JSON.stringify(labels, null, 2))
{% endhighlight %}

You will get a JSON blob looking like something like this: [https://github.com/springload/labels/blob/master/labels.json] [6]

Feel free to reuse directly Springload's blob. We try to keep it as standard as possible :)

You can also write your own config from scratch if you feel like it. Just make sure to respect [this pattern] [7].

#### Use the config

Once you have your config saved at the root of your project as `labels.json` and you have run `npm install -g github-label-sync`, it's time to import the labels inside your repository.

To do so, run this command `github-label-sync --access-token xxxxxx myname/myrepo`.
If you want to see what will happen before actually executing it, you can run a dry run with `github-label-sync --access-token xxxxxx --dry-run myname/myrepo`

You should get something like this:

{% highlight shell %}
Syncing labels for "springload/springtunes"
Fetching labels from GitHub
 > Missing: the "★★★" label is missing from the repo. It will be created.
 > Missing: the "★★☆" label is missing from the repo. It will be created.
 > Missing: the "★☆☆" label is missing from the repo. It will be created.
 > Missing: the "0 - Backlog" label is missing from the repo. It will be created.
 > Missing: the "1 - Ready" label is missing from the repo. It will be created.
 > Missing: the "2 - Working" label is missing from the repo. It will be created.
 > Missing: the "3 - To be tested" label is missing from the repo. It will be created.
 > Missing: the "4 - Testing" label is missing from the repo. It will be created.
 > Missing: the "5 - Tested" label is missing from the repo. It will be created.
 > Missing: the "6 - Live" label is missing from the repo. It will be created.
 > Missing: the "BED" label is missing from the repo. It will be created.
 > Missing: the "Big" label is missing from the repo. It will be created.
 > Changed: the "bug" label in the repo is out of date. It will be updated to "Bug" with color "#fc2929".
 > Missing: the "Content Update" label is missing from the repo. It will be created.
 > Missing: the "Design" label is missing from the repo. It will be created.
 > Changed: the "duplicate" label in the repo is out of date. It will be updated to "Duplicate" with color "#cccccc".
 > Changed: the "enhancement" label in the repo is out of date. It will be updated to "Enhancement" with color "#84b6eb".
 > Missing: the "FED" label is missing from the repo. It will be created.
 > Missing: the "Future" label is missing from the repo. It will be created.
 > Changed: the "help wanted" label in the repo is out of date. It will be updated to "Help wanted" with color "#cc317c".
 > Changed: the "invalid" label in the repo is out of date. It will be updated to "Invalid" with color "#e6e6e6".
 > Missing: the "Medium" label is missing from the repo. It will be created.
 > Missing: the "Feature name 1" label is missing from the repo. It will be created.
 > Changed: the "question" label in the repo is out of date. It will be updated to "Question" with color "#cc317c".
 > Missing: the "Small" label is missing from the repo. It will be created.
 > Missing: the "Tested & Failed" label is missing from the repo. It will be created.
 > Missing: the "Tested & Passed" label is missing from the repo. It will be created.
 > Missing: the "Won't fix" label is missing from the repo. It will be created.
 > Added: the "wontfix" label in the repo is not expected. It will be deleted.
Applying label changes, please wait…
Labels updated
{% endhighlight %}

If you want more options check the [documentation for github-label-sync] [8].

### Huboard

Now it's time for you to create some issues, label them nicely and strictly and then open [Huboard][2].
You will see something looking like [this][9].
With your issues, your colors and your own project stages, etc. ;)

HAPPY PROJECT MANAGEMENT!

  [1]: http://www.springload.co.nz
  [2]: https://www.huboard.com
  [3]: https://www.github.com
  [4]: https://www.npmjs.com/package/github-label-sync
  [5]: https://gist.github.com/MoOx/93c2853fee760f42d97f
  [6]: https://github.com/springload/labels/blob/master/labels.json
  [7]: https://github.com/Financial-Times/github-label-sync/blob/master/labels.json
  [8]: https://github.com/Financial-Times/github-label-sync#command-line-interface
  [9]: https://huboard.com/huboard/huboard


