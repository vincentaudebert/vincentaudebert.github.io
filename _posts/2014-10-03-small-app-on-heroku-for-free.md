---
layout: post
title: Small app on Heroku for free
date:       2014-10-03 15:31:19
summary:    Get your app set up on Heroku using only free services
categories: heroku free hosting
---

I got into Heroku a few weeks ago now and I think it's time to give you my feedback.

I remember when I started web development pretty much 10 years ago, deploying websites was a real pain and you had to cross your fingers really strongly to not crash your website for few minutes or hours/days in the worst cases.

Nowadays, thanks to big improvements in web technologies, by using a performant fullstack like [MEAN.io] [1] or [Ruby on Rails] [2] and a GIT based host like [Heroku] [3] you can deploy your app using only 1 command line like this one for Heroku: `git push heroku master`

That's magic, really efficient, good for your nerves and your brain and also AFFORDABLE!

Indeed, Heroku offers a free starter option which allows you to play a bit with their backoffice and see how it works. This offer (1 free dyno) is perfect for small apps or low traffic websites and once again, is completely free. So what are the cons? After the potential lack of power for high traffic website, the main one is that if you have only the free dyno, this one will go asleep after 1 hour of non activity on your app. Pretty bad and to get out of its idling state on the next loading, it can take sometimes more than 7 seconds!

###What's the trick?

Thanks god there is really easy and free work around to avoid your dyno to go into his sleep mode. This is called "Monitoring". Basically, monotoring your app will call it every X minutes to check if your server is still up and will record response time and many other data.

One good free monitoring service is [UptimeRobot] [4]. It's currently pinging my heroku server every 45mins and keeping my response time under 200ms. By calling my server every 45mins I prevent it idling and keep it efficient/awake for the next "real" call.
As I was saying in this [previous post][8] (cf Bonus point #2), Heroku has a great response time.

###What about the database?

Once you've solved this idling problem, you will face some other small problems like finding a free Heroku add-on for your database.
By default Heroku includes a [Postgres SQL database] [5] which is free for less than 10 000 rows which should be enough for small apps.

What I recommend is just switching to [MEAN.io] [1] and install the database add-on [MongoLab] [6] which is free under 500MB.

You will work only using Javascript and MEAN is a really powerful project starter for small apps. And Heroku accepts node.js apps so no excuses! :)

###Bonus service that I really like

If you want to upload files really easily, Heroku recommends using Amazon S3. Of course, it depends of your needs but I highly recommend [FilePicker.io] [7] which is another free add-on if you upload less than 500 files / month and your files are lighter than 20MB. They provide all the file upload system to S3 + the UI and just return a URL and file properties. Ready to use and provides you data to store in your MongoDB or to use directly in your app!


  [1]: http://mean.io
  [2]: http://rubyonrails.org/
  [3]: http://heroku.com/
  [4]: http://uptimerobot.com/
  [5]: https://addons.heroku.com/heroku-postgresql
  [6]: https://addons.heroku.com/mongolab#sandbox
  [7]: https://addons.heroku.com/filepicker
  [8]: http://vincentaudebert.github.io/frameworks/node/angular/nosql/2014/09/26/mean-io-it-is-mean/
