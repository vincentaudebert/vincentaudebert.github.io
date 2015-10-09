---
layout: post
title: SqlAlchemy cascade delete
date:       2015-10-09 15:31:19
summary:    Getting a foreign key error when deleting an object with dependencies?
categories: python sql
---

Quick tip if you get in trouble with a foreign key dependency even if you specified a cascade delete in your models.

Using SQLAlchemy, to specify a cascade delete you should have `cascade='all, delete'` on your parent table.
Ok but then when you execute something like:

{% highlight python %}
session.query(models.yourmodule.YourParentTable).filter(conditions).delete()
{% endhighlight %}

It actually triggers an error about a foreign key used in your children tables.

The solution I used it to query the object and then delete it:
{% highlight python %}
session = models.DBSession()
your_db_object = session.query(models.yourmodule.YourParentTable).filter(conditions).first()
if your_db_object is not None:
	session.delete(your_db_object)
{% endhighlight %}

This should delete your parent record AND all the children associated with it.