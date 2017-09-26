---
layout:  session
session_number: 2
title:   Backends for Mobile Applications (aka Pocket Cloud Computing)
session: true
classpath: MPCS51032/2017-Spring
---

Session Materials
=================
* Session 2 [Slides]({{ site.cdn }}/sessions/session2/MPCS51033-2017-Spring-Lecture2.pdf)
* [Class Playground Repository]({{site.playground}})

Links
=====
* [App Engine charges $6,500 to update a ListProperty on 14.1 million entities  Hacker News](https://news.ycombinator.com/item?id=3431132)


Resources
=========
* Google Cloud Platform Videos
  - [Navigating Google Cloud Platform: a guide for new GCP users (Google Cloud Next '17) - YouTube](https://www.youtube.com/watch?v=5NQHi_zDGy0&t=2641s&list=PLIivdWyY5sqI8RuUibiH8sMb1ExIw0lAR&index=17)
  - [Google Cloud Next ’17  "Where should I run my code?" Deciding between Compute Engine, Container Engine, App Engine and more ](https://cloudnext.withgoogle.com/schedule#target=where-should-i-run-my-code-deciding-between-compute-engine-container-engine-app-engine-and-more-91e716a3-813e-43c9-a513-27d3365a449b)
  - [Developing made easy on Google Cloud Platform (Google Cloud Next '17)](https://www.youtube.com/watch?v=ykzCUFwHppI&t=16s&list=PLIivdWyY5sqI8RuUibiH8sMb1ExIw0lAR&index=119)

* Google App Engine Standard Environment
  - [App Engine - Build Scalable Web & Mobile Backends in Any Language     Google Cloud Platform](https://cloud.google.com/appengine/)
  - [Google App Engine Python Standard Environment Documentation     App Engine standard environment for Python    Google Cloud Platform](https://cloud.google.com/appengine/docs/standard/python/)

* Google App Engine Concepts
- [Concepts     App Engine standard environment for Python     Google Cloud Platform](https://cloud.google.com/appengine/docs/standard/python/concepts)
 - [An Overview of App Engine An explanation of App En](https://cloud.google.com/appengine/docs/standard/python/an-overview-of-app-engine)
 - [The Python Runtime Environment A description of th](https://cloud.google.com/appengine/docs/standard/python/runtime)
 - [How Requests are Handled How requests to your appl](https://cloud.google.com/appengine/docs/standard/python/how-requests-are-handled)
 - [How Requests are Routed How HTTP requests from use](https://cloud.google.com/appengine/docs/standard/python/how-requests-are-routed)
 - [How Instances are Managed A description of how App](https://cloud.google.com/appengine/docs/standard/python/how-instances-are-managed)
 - [Access Control Set access control using roles at t](https://cloud.google.com/appengine/docs/standard/python/access-control)
 - [Application Security Steps you should take to iden](https://cloud.google.com/appengine/docs/standard/python/application-security)


Assignment 2
============

## Part 1 ##
As discussed in class, there are some potential issues with our photo timeline backend. In the fist part of the assignment you will update our existing code base ([available here on Github](https://github.com/uchicago-cloud/uchicago-cloud-photo-timeline)) with the following changes.

### Update the Data Model ###
Our data model works fine for a small number of users, but if (when ) our app goes viral, querying for a users photos will be inefficient and potentially costly.  While we can count on the built-in query memcache and our own memcache solution, we can head off the problem by making changes to our data model.

* Add a `User` model to the application with the following properties:
  - `name`
  - `email`
  - `unique_id` (you can choose to use the `Key` property instead)
  - `photos` (reference to a collection of the users photos)
  - `username`
  - `password`
  - `id_token` (a unique urlsafe string that anonymously identifies this user)

* Update all the queries to take advantage of the new `User` model

* Update the `Photo` model to reflect the `User` model.  We will no longer need to keep track of the user who took the photo.  Remember that every bit of data we store has a resource and economic cost.

### Improve Security for Users ###
Currently our app offers no security to protect our users or our resources.  Anyone with the API can post and retrieve any users pictures.  

* Add an authentication API that passes a username and password and (if successful) returns a unique token. This token would be stored on the users device and passed as a parameter on all API requests.

```
http://--.appspot.com/user/authenticate/?username=XXX&password=XXXX
```

* Update all API calls to require the token to be passed as a parameter as follows:

```
# Get a json list of most recent submitted pictures
http://--.appspot.com/user/<USERNAME>/json/?id_token=XXXX


# See a list of the most recent on a web page (useful for debugging
http://--.appspot.com/user/<USERNAME>/web/?id_token=XXXX

# Endpoint for posting images to server. There is an optional "caption" parameter that you can use.
http://--.appspot.com/post/<USERNAME>/?id_token=XXXX
```

* Update the application to validate any request by testing that the token is valid (ie is in the database).

### Allow Users to Delete Photos ###
If Snapchat made ephemeral pictures worth a billion dollars, than maybe our approach of not deleting any photos will be worth 2 billion dollars.  Or...maybe it will cost us 2 billion in storage costs.  

* Expand the API to allow users to delete photos by passing the photo key.
```
# Add ability to delete a photo
http://--.appspot.com/image/<key>/delete/?id_token=XXX
```

### Mobile Client ###
You do not have to built a mobile client to interact with the API.   The API will be tested using `curl`, the (amazing) web interface and App Engine console.  I would encourage you to use these during development.  

Example `curl` commands:

```
# Get the webform (not too useful)
curl -X GET http://localhost:8080/

# Download the json representing the users photos
curl -X GET http://localhost:8080/user/default/json/?id_token=XXXXX

# Upload using a multpart form (note that you need to put the absolute path of the image)
curl -X POST -H "Content-Type: multipart/form-data" -F caption='curl' -F "image=@kitten.jpg"  http://localhost:8080/post/lolakitty/?id_token=XXXX
```

### Grading ###
The application should complete all of the requirements and function without errors.  The application should function on a local development server and have a version running on Google App Engine.  

Companion mobile apps should compile with no errors or warnings and perform all described behaviors.

Feel free to explore additional enhancements to improve the appearance or functionality of the application.

## Part 2 ##
In this part of the assignment, you will create a custom mobil application analytics platform.  You will be responsible for the design and implementation of the backend.

The analytics platform will track the following:
  * Track unique users - visits, time duration
  * Track events - clicks, navigation
  * Touch heat map - track touches
  * Send a daily email summary of all the user activity in your app

More specific details about further requirements will be discussed next week.


### Due Date ####
Assignment 2 is due **April 19, 2017 at 5:29pm.** Use the assignment repos in GitHub to submit your assignment.  Please inlcude the URL of the applications in their respective README.md file.
