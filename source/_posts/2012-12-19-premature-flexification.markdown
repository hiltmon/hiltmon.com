---
layout: post
title: "Premature Flexification"
date: 2012-12-19 10:42
comments: true
categories: [ Software, Design ]
---

I was sitting down to design an iOS widget to display an analogue clock face for an upcoming app. I wanted to make sure, as we all do, that the widget will work for all scenarios needed by the app. The app needs to display the time in different time zones, given a reference time in a reference timezone.

✓ User defined background image and hand images  

**STOP!** *You Aren't Gonna Need It.* It’s my widget for my app, it’s OK to hardcode the image assets.

✓ Draw hour hand  
✓ Draw minute hand  
✓ Draw second hand  

**STOP!** *You Aren't Gonna Need It.*  The clock face will display a fixed time up to the minute. No need for a second hand then.

✓ Timezone and DST support  
✓ Timer to update the face  

**STOP!** *You Aren't Gonna Need It.*  The application needs to display a clock face for a time in the past or future which does not change, no need to be live.

✓ Scaling to fit variable view sizes  

**STOP!** *You Aren't Gonna Need It.*  The application will display the clock in 2 sizes, large and small. No need for complex scaling code.

✓ Hand wobble as hands move to new locations (that little vibration that is caused by the flexibility in the hand when it comes to rest)  

**STOP!** *You Aren't Gonna Need It.*  I can animate the hour and minute hand using rotation code (which will already be used to align the hands) to get them into position, no need to add a skeuomorphic wobble when the hand comes to rest.

**I wrote this to remind myself not to prematurely flexify classes.** [YAGNI](http://c2.com/cgi/wiki?YouArentGonnaNeedIt) FTW!

*Follow up: [How to Flexify a Class](http://www.hiltmon.com/blog/2012/12/19/how-to-flexify-a-class/) tells you what to do when the day comes that you do need to add features or flexibility to a class.*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
