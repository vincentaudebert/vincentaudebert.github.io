---
layout: post
title: Jest coverage fails
date:       2016-12-13 10:31:19
summary:    Unknown component instead of your component name?!
categories: javascript jest
---

Probably my last quick post of the year 2016! Yay for 2017!

Recently I really got into unit testing and [Jest] [4].

What a wonderful tool! Especially to test React components! As easy as [.toMatchSnapshot()] [1]! Those who did some component testing using Mocha+Chai know what I'm talking about.

Although, I faced an annoying problem recently.

## `jest` passes but `jest --coverage` fails

You run your tests with `jest`. Snapshots are generated properly and tests are passing like you expect them to do.

Life is cool.

Then you run `jest --coverage` and suddenly you get something like this:

```
 FAIL  jest/CatBar.spec.js
  ● CatBar component › renders correctly with min params

    expect(value).toMatchSnapshot()

    Received value does not match stored snapshot 1.

    - Snapshot
    + Received

    @@ -1,13 +1,13 @@
     <div
       className="catbar">
       <p>
         I'm a cat bar. I contain cats.
       </p>
    -  <StatelessAnimal
    +  <Unknown
         sound="Meow!" />
    -  <StatelessAnimal
    +  <Unknown
         sound="Meoooow!" />
    -  <StatelessAnimal
    +  <Unknown
         sound="Meeeeeeeeow!" />
       <HatchingAnimal />
     </div>

      at Object.<anonymous> (jest/CatBar.spec.js:11:24)
      at process._tickCallback (internal/process/next_tick.js:103:7)
```
(This is generated on purpose using [this cool learning repo about Jest] [2].)

Your tests are failing because the `jest --coverage` isn't matching the same component names than your normal `jest`. It looks for `Unknown` instead of your component name...

## Solution: displayName

The solution is very simple even if a tiny bit annoying.

You need to specify a `displayName` property on your stateless component. [Like I did here] [3] to make my tests to pass with `--coverage`.

```
StatelessAnimal.displayName = 'StatelessAnimal';
```

Then if you run your tests again using `--coverage` it should pass.

Just make sure you don't make any typo mistake :)

Originally found the solution on these posts: [https://github.com/facebook/jest/issues/1740] [5] and [https://github.com/facebook/jest/issues/1824#issuecomment-250376673] [6] 

  [1]: http://facebook.github.io/jest/docs/api.html#tomatchsnapshot
  [2]: https://github.com/springload/mocha-chai-to-jest
  [3]: https://github.com/springload/mocha-chai-to-jest/blob/ddc555ab6d28da3498174d2622bf73b854db6c13/things-to-test/StatelessAnimal.js#L16
  [4]: http://facebook.github.io/jest/
  [5]: https://github.com/facebook/jest/issues/1740
  [6]: https://github.com/facebook/jest/issues/1824#issuecomment-250376673
