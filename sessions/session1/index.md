---
layout: session
session_number: 1
title:   Welcome to Backends for Mobile Application
session: true
---

Session Materials
================================================================
* Session 1 [Slides]({{ site.cdn }}/sessions/session{{session_number}}/mpcs51033-2017-autumn-lecture-1.pdf)

Interesting Links
================================================================
* [App Engine charges $6,500 to update a ListProperty on 14.1 million entities  Hacker News](https://news.ycombinator.com/item?id=3431132)

Resources
=========
* Google Cloud Platform Videos
  - [Navigating Google Cloud Platform: a guide for new GCP users (Google Cloud Next '17) - YouTube](https://www.youtube.com/watch?v=5NQHi_zDGy0&t=2641s&list=PLIivdWyY5sqI8RuUibiH8sMb1ExIw0lAR&index=17)
  - [Google Cloud Next ’17  "Where should I run my code?" Deciding between Compute Engine, Container Engine, App Engine and more ](https://cloudnext.withgoogle.com/schedule#target=where-should-i-run-my-code-deciding-between-compute-engine-container-engine-app-engine-and-more-91e716a3-813e-43c9-a513-27d3365a449b)
  - [Developing made easy on Google Cloud Platform (Google Cloud Next '17)](https://www.youtube.com/watch?v=ykzCUFwHppI&t=16s&list=PLIivdWyY5sqI8RuUibiH8sMb1ExIw0lAR&index=119)

* Google App Engine on Google Cloud Platform
  - [App Engine - Build Scalable Web & Mobile Backends in Any Language     Google Cloud Platform](https://cloud.google.com/appengine/)

* Google App Engine Standard Environment
  - [Google App Engine Python Standard Environment Documentation     App Engine standard environment for Python Google Cloud Platform](https://cloud.google.com/appengine/docs/standard/python/)

* Important Concepts in Google App Engine for Python
  - [App Engine standard environment for Python Google Cloud Platform](https://cloud.google.com/appengine/docs/standard/python/concepts)
  - [An Overview of App Engine](https://cloud.google.com/appengine/docs/standard/python/an-overview-of-app-engine)
  - [The Python Runtime Environment](https://cloud.google.com/appengine/docs/standard/python/runtime)
  - [How Requests are Handled How](https://cloud.google.com/appengine/docs/standard/python/how-requests-are-handled)
  - [How Requests are Routed](https://cloud.google.com/appengine/docs/standard/python/how-requests-are-routed)
  - [How Instances are Managed](https://cloud.google.com/appengine/docs/standard/python/how-instances-are-managed)
  - [Access Control Set](https://cloud.google.com/appengine/docs/standard/python/access-control)
  - [Application Security](https://cloud.google.com/appengine/docs/standard/python/application-security)


Assignment
================================================================================
* Sign up for GitHub

* [Sign up](https://join.slack.com/t/mpcs51033-2017-autumn/shared_invite/enQtMjQ2OTkwNjIwMzA2LTA5MTNiZjRkOTA3ZDQ4Yzc1ZmNhZjNjMjU4OTc3MTc0ZjM5MTg2ZTg1OTVlYTg4YmM5NzFkNTIwOTU0N2E0NWE) for Slack and join the class team
  - Post an introductory message in `#general`.  Tell us a little about yourself and some things you are interested in learning in this course.
  - Send me a direct message with you GitHub user id so I can add you to classroom.

* Sign up for GCP account and add educational credits
  - Link is in Slack #general

* Review the documentation for [Python on Google App Engine](https://cloud.google.com/appengine/docs/python/) for the [Standard Environment](https://cloud.google.com/appengine/docs/standard/python/).  
>There is quite a bit of fragmented information about App Engine in the documentation so there isn't a linear path to reading it.  You should just try to become familiar with some of the capabilities and terminology, we will review it in the first class.

* Complete the following tutorial: [Hello World](https://cloud.google.com/appengine/docs/standard/python/tutorials).   This is a quick start tutorial and there is nothing to turn in.

* Complete the following tutorial: [Guestbook tutorial](https://cloud.google.com/appengine/docs/standard/python/tutorials).  In addition the tutorial as written, please add the additional features:
  - Update the `Greeting` data model by adding a property named `user_agent` that includes the HTTP user agent.  This is useful to determine which browser and device is making a request (ie. detect a mobile device).  The `user_agent` should be a string type.

*  You do not have to built a mobile client to interact with the Guestbook application, however, it is often useful to develop tools that allow you to rapidly test web services and APIs with having to physically switch clients.  Develop command line statements using the UNIX `curl` command to interact with the guestbook.

  Example `curl` commands:

  ```
  # Get a content from a URL
  curl -X GET http://localhost:8080/

  # Upload using a multipart form (note that you need to put the absolute path of the image)
  curl -X POST -H "Content-Type: multipart/form-data" -F key1='value1' key2='value2'
  ```
  Write out the commands you used in the repository `README.md` file.

* Familiarize yourself with GCP (as needed).
> These are just some suggestions that will prepare you better for next week.  Watch and/or read whatever you feel you need to.  There are more resources listed above.

  - Watch: [Navigating Google Cloud Platform: a guide for new GCP users (Google Cloud Next '17) - YouTube](https://www.youtube.com/watch?v=5NQHi_zDGy0&t=2641s&list=PLIivdWyY5sqI8RuUibiH8sMb1ExIw0lAR&index=17)
  - Brush up on Python programming.
  - Explore the GCP Console (especially Cloud Shell)


### Grading ###
The guestbook application should complete all of the requirements and function without errors.  The application should function on a local development server and have a version running on Google App Engine.  Please include the URL in the `README.md` file.

Feel free to explore additional enhancements to improve the appearance or functionality of the application.

If you have any questions, please ask in #assignment channel on Slack.

### Due Date ####
Assignment 1 is due **October 3, 2017 at 5:29pm.** Use the assignment repos in GitHub to submit your assignment.  Please include the URL of the deployed applications in a `README.md` file.
