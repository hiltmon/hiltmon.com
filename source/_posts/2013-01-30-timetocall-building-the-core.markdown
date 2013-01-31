---
layout: post
title: "TimeToCall - Building the Core"
date: 2013-01-30 11:29
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall](http://www.hiltmon.com/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is is [part 2 is a series of posts](http://www.hiltmon.com/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iOS app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software.*

## The Core Was Easy

Building the core code for [TimeToCall](http://www.hiltmon.com/timetocall/) was most certainly the easiest part of the whole process. The iOS libraries are spectacularly easy to work with and the architecture of the application is very simple.

In this post, I'll give an overview of the default app that Xcode provides and the areas customized. Although this part of the series *may* be the most technical, I hope show that there is a lot of work that needs to be done to change the default app into something beautiful.

If I had to pull out a lesson from this, I would say that I spent too much time at the start worrying about the core and estimating that, and not in investigating the nuances and customizations required.

## The Core Program

[TimeToCall](http://www.hiltmon.com/timetocall/) started life as a standard iOS “Master-Detail Application”, universal (so iPad and iPhone), ARC enabled, with StoryBoards and Core Data off. I turned Core Data off because the data model is too simple, and I turned StoryBoards off because I used them in the last project and was planning on writing this one without `Xib` files (think of these as visual GUI files, but they are a whole bunch more).

Without writing a single line of code, this standard iOS app gives you a Master and Detail view controller, rotation, popovers, iPhone and iPad Xibs and a simple array of objects as the data model. That's brilliant.

So all I had to do in the core was build the flow.

{% img /images/timetocall-controllers.jpg 738 310 %}

The core flow consists of four views:

* A main view controller that manages the display of the list of *Times to Call*
* A detail view controller that displays the current *Time to Call* and allows you to ‘play' with time or run the optimizer
* A view controller for editing the *Time to Call*, and
* A view controller for picking places.

To support the views, I created the original model code:

* A class to represent a `CallZone` (name, source location, time and list of destinations)
* A class to store and search the timezones for the picker
* Some code to load and save the array of `CallZones`
* Some code to display the time shifts for each destination

That's all there is to the core of the application. I developed the views using standard iOS components in a few hours, and the model code took a few hours more. By the third day of part-time development, I had a working app.

## Making it Pretty

But the default iOS look and feel does not cut it these days. People expect colors and fonts and animations and shapes and images. Default apps look old and boring. Kinda funny considering that iOS is only 5 years old.

So, I needed more classes to customize the presentation of the data:

* A Custom Table View Cell for Master to display each `CallZone` and some of their times
* A Custom Table View Cell for Detail to display each destination's time
* A Custom view to present the clock

Each of these has an iPhone and an iPad version. But I got smart and reused the same View Controller code, so I felt I was ahead.

These custom view classes are *hard to design* and *easy to code*. How to present the data? How to make it cool? How to make understandable? That used up a lot of hours and I'll go into the thinking behind these in later parts of this series.

So, surely I was done. The core was written, the app ran and looked reasonable.

## Not So Fast

It was not all smooth sailing, easy peasy or whatever the best phrase is for nothing going wrong. **Even the simplest applications have hidden complexities**.  The place data was awful, the time conversion code was a mess and I had so much code copied and pasted throughout the core that it was difficult to make changes across only four simple views.

Lets look at each in detail and the lessons learned:

### Never Make Assumptions

When I kicked off the project, I *assumed* that the city names I needed would all appear in the standard Unix timezone database, because “how else does Apple handle the city to timezone mapping on iOS” in setup. I even loaded the database into [BBEdit](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fbbedit%252Fid404009241%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30) and searched for a bunch of major cities and they all came up. So I wrote the core around this data set.

How wrong was I.

There are only 411 entries in the TimeZone database, but a lot more major cities. 

I had forgotten to follow my own rule: *Never make assumptions*.

I needed a database of places that we humans think of with a mapping to timezones that the product can use. Fortunately, it exists, and it did not delay development to get it. I downloaded the [GeoNames](http://www.geonames.org/) database, and created a script to pull out all cities where the population is over a certain size. With a little experimentation, I settled on 100,000 population and used that as the place model data (4,184 places). Just to be sure, I then checked that each of these cities had timezones that existed in the timezone database so that the mapping would work.

### Standardizing the Data Model

[TimeToCall's](http://www.hiltmon.com/timetocall/) computation is quite simple, it takes a time in a given timezone and displays the same time in other timezones and calculates earlier or later for optimization. To make it even easier, the iOS libraries have `NSCalendar`, `NSDateFormatter`, `NSTimeZone`, `NSDateComponents` and `NSDate` classes that can be combined to do this conversion and presentation.

Or not.

Because the `NSDate` is immutable, you can create it, and use `NSDateFormatter` to present it, but you cannot change it. Which means you cannot just change the `NSTimeZone` on an `NSDate` to see the new time. Thats okay, you can use a different `NSTimeZone` in a `NSDateFormatter` to present the new time. But that produces strings, and I also needed numerics to determine earlier or later.

Skipping the boring details, I found that I was writing a lot of code that switched the user's call time between timezones to calculate offsets. In essence, I had a timezone and an `NSDate` in too many places, in the source timezone (calling from), in the `NSDate` object that stores the call time and in each timezones that you are calling to. I wrote a lot of code to ensure that the `NSDate` timezone in the main object used the right timezone, and the calculated `NSDates` for display used the appropriate ones for each call-to, and used these for offsets.

Too many conversions, too many opportunities for things to go wrong. And they did.

So I simplified it by making the internal `NSDate` object's timezone null (or GMT). Which meant that I would only ever have to do a single conversion, GMT to timezone, or back to GMT for computation, which happens to be available through `NSDate` . It means that the optimizer and the debugger log GMT times when debugging, but the code is a lot smaller, slimmer and less failure prone.

### Pulling Out the Model

The primary object on the system is a `CallZone`, consisting of a user supplied name, source place, call time, and a list of destination places. All else is calculated on the fly. I save and load an array of these into a standard `.plist` file in the app. A very simple data model.

The default iOS application’s model is an array of generic objects, and this is instantiated in the Master view controller (where you see the list of `CallZones`). The older version of the default iOS application had this in the Application Delegate, a class that kicks in when the app launches and quits. Both approaches work, but require you to pass this array between all controllers as you need them, and to have access to the ‘owning' controller to trigger saves (or use `NSNotificationCenter`).

So is the Master View the model? Or is the Application Delegate the model? Since the 1970's, we software types have been following [Trygve Reenskaug's](http://en.wikipedia.org/wiki/Trygve_Reenskaug) famous [Model-View-Controller](http://en.wikipedia.org/wiki/Model-view-controller) design pattern, yet the default iOS app seems to break this.

I prefer the right approach, to separate the model from the controllers and to use objects, not collections of native types for data. A True Model-View-Controller architecture. So I moved the array of `CallZone` objects and the load and save operation to a `NOVApplicationData` singleton class. I chose the singleton pattern for this as there can be only one set of data in this app, singletons are easy to access from anywhere and I do not have to pass the model around all the view controllers, they can all call up the singleton. And most importantly, I have a separate class for the model data and its operations.

### Refactoring Duplicated Code

If you look at the app, you'll see that both the Master and Detail views present data for a `CallZone`. They both display the clock, they both display the adjusted times, and they both display the images for the day period (morning, night). I had not created custom views for each because the layout of each was different. But I did have the same code in both of these views to determine *what* to display. Which meant, as I was iterating, that I would always have to change code in two places.

For a simple app like [TimeToCall](http://www.hiltmon.com/timetocall/), that's not really a problem. For a more complex app, duplicated code becomes a maintenance and iterative nightmare and actually *increases* to time to develop it. You have to *remember* to make the same change all over the place.

So I created another class to help with the presentation of a `CallZone`, with tools for displaying the time, managing the clock face, and displaying the image and time of day for each destination. This *helper* class is used by all tableview cells. With this modularized code, I can use the same class to help display the `CallZone` consistently without having to duplicate code in views. It also meant I could iterate on the customization a lot faster and get the product completed a lot quicker too.

[TimeToCall](http://www.hiltmon.com/timetocall/) will be on the App Store soon for 99c. In the mean time, feel free to follow this [series of posts](http://www.hiltmon.com/blog/categories/timetocall/) about making and polishing this app.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
