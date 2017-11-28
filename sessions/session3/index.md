---
layout:  session
session_number: 3
title:   Best Practices with App Engine
session: true
classpath: MPCS51032/2017-Spring
---

Session Materials
=================
* [Slides]({{ site.cdn }}/sessions/session3/mpcs51033-2017-autumn-lecture-3.pdf)

* Assignment 3 [write-up]({{ site.cdn }}/sessions/session3/mpcs51033-2017-autumn-assignment3.pdf)

Resources
=========
* Ancestor Keys
  - https://cloud.google.com/appengine/docs/standard/python/datastore/queries
  - https://cloud.google.com/appengine/docs/standard/python/datastore/data-consistency
  - [Structuring Data for Consistency](https://cloud.google.com/appengine/docs/standard/python/datastore/structuring_for_strong_consistency)

* Cursors
  - https://cloud.google.com/appengine/docs/standard/python/datastore/query-cursors#query_cursor_example

* API
  - [What is a rest API](https://tutorialedge.net/general/what-is-a-rest-api/)
  - [The Basics of REST and RESTful API Development](http://www.hongkiat.com/blog/rest-restful-api-dev/)
  - [APIs on Azure](https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design)
  - [Swagger](https://swagger.io)

* Microservices
  - [Microservices Architecture on Google App Engine](https://cloud.google.com/appengine/docs/standard/python/microservices-on-app-engine)
    -
  https://cloudplatform.googleblog.com/2016/06/creating-a-scalable-API-with-microservices.html
    - [Building scalable apps with Cloud Datastore (Google Cloud Next '17) - YouTube](https://www.youtube.com/watch?v=0EIqacNVuAo&t=11s)

* Sharding
  - [Sharding counters](https://cloud.google.com/appengine/articles/sharding_counters)
  - [High concurrency counters without sharding - Nick's Blog](http://blog.notdot.net/2010/04/High-concurrency-counters-without-sharding)


* Tasks
  -
[Using Pull Queues in Python](https://cloud.google.com/appengine/docs/standard/python/taskqueue/overview-pull)
-  [Background work with the deferred library -  App Engine Documentation  -  Google Cloud Platform](https://cloud.google.com/appengine/articles/deferred)


* Scheduling Cron Tasks
  - [Scheduling Tasks With Cron for Python](https://cloud.google.com/appengine/docs/standard/python/config/cron)




Assignment 2
============

## Part 2 ##

> Please see [the write-up]({{ site.cdn }}/sessions/session3/MPCS51033-2017-Spring-Assignemnt2-Part2.pdf)


You will create a custom mobile application analytics platform.  You will be responsible for the design and implementation of the backend.

The analytics platform will track the following:
  * Track unique users - visits, time duration
  * Track events - clicks, navigation
  * Touch heat map - track touches
  * Send a daily email summary of all the user activity in your app

### Due Date ###
Assignment 3 is due **October 19, 2017 at 5:29pm.** Use the assignment repos in GitHub to submit your assignment.  Please include the URL of the applications in the respective README.md file.
