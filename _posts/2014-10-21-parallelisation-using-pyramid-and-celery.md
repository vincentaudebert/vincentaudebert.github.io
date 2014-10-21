---
layout: post
title: Parallelisation using Pyramid and Celery
date:       2014-10-21 15:31:19
summary:    Split your big tasks in smaller ones and improve your processing time.
categories: python pyramid celery
---

Today let's see how you can use parallelisation to improve your processing time.

But first, let's talk languages and versions:
For this article, I'm using Python on version 2.7, the web framework Pyramid on version 1.5 and Celery on version 3.

Parallelisation is really powerful to reduce a lot your loading time/processing time.
Basically, without it, your code will be executed by one server. With parallelisation you split a task in many smaller ones to be processed by many virtual servers. There are many benefits but the main one is definitely to avoid loading locks on Database usage or CPU usage. This is really efficient on Amazon Web Services. Indeed, once a node is overloading in terms of tasks, AWS should create a new one and spread the tasks on all the nodes. I won't go too much in the details as it's not my expertise but for those interested, [you can have complementary info here] [1].

##Example case
So let's dive into the code. Let's say you have a warehouse with many products. You want to process each products by chunks instead of processing the whole warehouse and crashing your server.

You will split big task, let's call it `processWholeWarehouse()` into smaller tasks `processSomeProducts(start, end)` (processing only 500 products) and you will append all these small taks to a list:

{% highlight python %}
task_list = []
for x in range(0, warehouse_products.length, 500):
	start = x
	end = x+500

	#Note the .s() is a Celery shortcut for .subtask()
	task_list.append(processSomeProducts.s(start, end))
{% endhighlight %}

Once you have done that you want to create a group of tasks using this `task_list`:

{% highlight python %}
if len(task_list)>0:
	product_group = group(task_list)
{% endhighlight %}

And then if you want to execute a callback function (processFinished) at the end of all this tasks, you need to use `chain` from Celery.

{% highlight python %}
chain(product_group, processFinished.s()).apply_async()
{% endhighlight %}

The callback function is really usefull if you need to update your database or trigger an event to tell your app that tasks have been processed.

###Bonus point (the famous one ;))

Don't forget to add the header `@celery.task` to your method and you can give some params like `acks_late=True` and `max_retry=5` to requeue your task automatically if there is an error.

{% highlight python %}
@staticmethod
@celery.task(acks_late=True, max_retries=5)
def processSomeProducts(self, start, end):
	try:
		#Your actions
		return True
	except Exception as exc:
		#Error management/logging
		#Will retry in 60 seconds
		raise YourClass.processSomeProducts.retry(exc=exc, countdown=60)
{% endhighlight %}

It's recommended to do the same for `processFinished()`

You can find more documentation on these Celery functions [here] [2]

  [1]: http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/concepts.html
  [2]: http://celery.readthedocs.org/en/latest/userguide/canvas.html#the-primitives
