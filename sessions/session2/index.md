---
layout:  session
session_number: 2
title:   Google App Engine
session: true
classpath: MPCS51032/2017-Spring
---

Session Materials
================================================================
* [Slides]({{ site.cdn }}/sessions/session2/mpcs51033-2017-autumn-lecture-2.pdf)
* [Class Playground Repository](https://github.com/uchicago-cloud/mpcs51033-2017-spring-playground)

Resources
=========

* Building Scalable Apps (2011, but still relevant)
  - [Google I/O 2011: Scaling App Engine Applications - YouTube](https://www.youtube.com/watch?v=rP-kjrx9CRE&feature=youtu.be&app=desktop)

* Datastore
  - [Building scalable apps with Cloud Datastore (Google Cloud Next '17) - YouTube](https://www.youtube.com/watch?v=0EIqacNVuAo&t=11s)

* Google Cloud Endpoints
  - [About Cloud Endpoints Frameworks](https://cloud.google.com/endpoints/docs/frameworks/python/about-cloud-endpoints-frameworks)
  - [Google Cloud Endpoints: serving your API to the world (Google Cloud Next '17) YouTube](https://www.youtube.com/watch?v=bR9hEyZ9774)


* Tasks
  -
[Using Pull Queues in Python](https://cloud.google.com/appengine/docs/standard/python/taskqueue/overview-pull)

  -  [Background work with the deferred library  |  App Engine Documentation  |  Google Cloud Platform](https://cloud.google.com/appengine/articles/deferred)


* Scheduling Cron Tasks
  - [Scheduling Tasks With Cron for Python](https://cloud.google.com/appengine/docs/standard/python/config/cron)

* [Google Vision API](https://cloud.google.com/vision/)

Assignment 2
================================================================================

Part 1
--------------------------------------------------------------------------------
As discussed in class, there are some potential issues with our photo timeline backend. In the fist part of the assignment you will update our existing code base ([available here on Github](https://github.com/uchicago-cloud/uchicago-cloud-photo-timeline)) with the following changes.

### Update the Data Model ###
Our data model works fine for a small number of users, but if (when ) our app goes viral, querying for a users photos will be inefficient and potentially costly.  While we can count on the built-in query memcache and our own memcache solution, we can head off the problem by making changes to our data model.

* Add a `User` model to the application with the following properties:
  - `name`
  - `email`
  - `unique_id` (you can choose to use the `Key` property or use a custom uuid)
  - `photos` (reference to a collection of the users photos)
  - `username`
  - `password`
  - `id_token` (a unique urlsafe string that anonymously identifies this user)

![](assets/index-dcf26529.png)

* Update the `Photo` model to reflect the new `User` model.  We will no longer need to keep track of the user who took the photo since we will have a reference to it from the `User` object.  Remember that every bit of data we store has a resource and economic cost.

* Update all the queries to take advantage of the new `User` model

### Update the Image Storage Strategy ###
Storing our images in Datastore is rather expensive compared to other storage options.  Change the way photos are stored in our backend so we take advantage of Google Cloud Storage.  Instead of storing image data in our `Photo` model, store a reference to the image stored in Google Cloud Storage.

> Note that you will have to enable additional APIs and services from the console to accomplish this.

### Improve Security for Users ###
Currently our app offers no security to protect our users or our resources.  Anyone with the API can post and retrieve any users pictures.  

* Add an authentication API that passes a username and password and (if successful) returns a unique token.

![](assets/index-7bd19791.png)

This token would be stored on the users device and passed as a parameter on all future API requests.  The unique token is represented in our datastore as `unique_id`.  

* The authentication API call should take the following form:

```
http://--.appspot.com/user/authenticate/?username=XXX&password=XXXX
```


> You can assume that the validation is always successful for the assignment. That is, the password is always correct.

* Update all API calls to require the token to be passed as a parameter as follows:

```
# Get a json list of most recent submitted pictures
http://--.appspot.com/user/<USERNAME>/json/?id_token=XXXX


# See a list of the most recent on a web page (useful for debugging
http://--.appspot.com/user/<USERNAME>/web/?id_token=XXXX

# Endpoint for posting images to server. There is an optional "caption" parameter that you can use.
http://--.appspot.com/post/<USERNAME>/?id_token=XXXX
```

* Update the backend  application (in all appropriate places) to validate any request by testing that the token is valid (ie. is in the database).  If the user makes an API call without an `id_token` return a HTTP Code of 401 Unauthorized access.


### Allow Users to Delete Photos ###
If Snapchat made ephemeral pictures worth a billion dollars, than maybe our approach of not deleting any photos will be worth 2 billion dollars.  Or...maybe it will cost us 2 billion in storage costs.  

Expand the API to allow users to delete photos by passing the photo key.
```
# Add ability to delete a photo
http://--.appspot.com/image/<key>/delete/?id_token=XXX
```

>Remember that deleting the photo should remove it from storage and remove any references to it in the `User` model.


### Automated Photo Labeling with Google Vision ###
Use the [Google Vision API](https://cloud.google.com/vision/docs/labels) to detect and identify labels in your users images.  
* Create a new `labels` property on the `Photos` object. `labels` should be a repeated string data type.
* When a user uploads a new photo you should create a task to analyze the photo and add top 3 scoring label descriptions to the photo's `labels` property.

### Mobile Client ###
You do not have to built a mobile client to interact with the API.   The API can be tested using `curl` and the web interface and App Engine console.  I would encourage you to use these during development.  

See the `README.md` file for more example `curl` commands.

>Note: You will be building a barebones iOS application to interact with the API for next week's assignment, so you can get started now if you choose.  I would recommend revisiting your old GitHub Issues application as a starting place.

### Grading ###
The application should complete all of the requirements and function without errors.  The application should function on a local development server.  Please include a list of all the `curl` commands that can be used to test the application in the `NOTES.md` file.

You should have a deployed version running on Google App Engine.  Please include the URL to the deployed version in the `NOTES.md` file.


Companion mobile apps or scripts should compile with no errors or warnings and perform all described behaviors.

Feel free to explore additional enhancements to improve the appearance or functionality of the application.


### Due Date ####
Assignment 2 is due **October 10, 2017 at 5:29pm.** Use the assignment repos in GitHub to submit your assignment.  Remember to include the requested information in the `NOTES.md` file. their respective README.md file.
