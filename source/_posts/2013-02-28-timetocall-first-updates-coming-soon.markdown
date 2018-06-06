---
layout: post
title: "TimeToCall - First Updates Coming Soon"
date: 2013-02-28 17:57
comments: true
categories: [ TimeToCall ]
---

I've received some great feedback and a few bug reports on TimeToCall and spent some time trying to make it a better product. The next decision is *when* to pull the trigger and put the first update through the App Store review process.

## Changes

The two big changes I have made so far are a *more accurate slider* and the *time now toggle*.

In the original release, I set the time slider to jump to 15 minute increments to make it easier to hit a 'zero' time. I did this because I could never get the tiny slider to hit the time I wanted with my own fat fingers. But people did not like it, they felt the slider did not behave very well.

I tried several solutions, but none made me happy. Then one of my users pointed out that the Apple podcasts app solved this accuracy problem by making the slider less sensitive the further down below the slider you moved your finger *whilst sliding*. Lovely idea, I had been trying to find a good way to do this. So I implemented that in TimeToCall, and it works much better than the old slider. The video below quickly shows the differences in sensitivity between close to the slider and further away:

<iframe width="420" height="315" src="http://www.youtube.com/embed/cNyd2OhHsCY?rel=0" frameborder="0" allowfullscreen></iframe>

As the sensitivity drops, the color on the slider cools to show the change.

Several other users have asked to see the from and to *Times to Call* as of right now, to see if they can call *now* instead of the scheduled time. The original release had this by double-tapping the slider handle, but no-one found it. So I made it explicit (and the app remembers the state between launches). Tap the clock to toggle live view, and the calendar to toggle back.

<iframe width="420" height="315" src="http://www.youtube.com/embed/hy-PbQkcTc0?rel=0" frameborder="0" allowfullscreen></iframe>

I also added a first-run overlay to explain these changes. Hopefully people will read it before tapping it away.

Other changes and bug fixes include:

* The green plus icon when editing places now works when you tap it.
* The display time-now spins the clocks a maximum of one day, not several.
* If you change the *calling from* location, the calling from time remains as it was and does not change. This means that the scheduled times all do get changed, but users seem to prefer this as they get to play with time again.
* <del>Doubled the number of places in the database, now using a 50,000 population filter.</del> Pulled this update at the last minute because the search was too slow (it's already too slow on the first character typed). And for the record, TimeToCall does *not* use any data bandwidth, the places database is included in the app.
* Enabled live time and state changes for more recent devices. On older devices, only the main time changes when you slide. On newer devices, all the times and states change as you play with time.
* Some new artwork, to make it look cooler, I hope.

## To Update or Not To Update, that is the Question?

I think the new slider and time-now views make this a good update candidate, especially since the two most annoying bugs are also fixed,  but is it enough? 

You see, even if I submitted it to Apple today, it will be a week to 10 days before my users get to see it (assuming the review passes). But if I don't submit it today, when? How many more changes are needed to make an *update-and-wait* cycle worthwhile for you and for me.

Since there are glaring bug fixes already completed, and I want these annoyances out of my users' way, I think it's best to get these fixes out there. So I'm pulling the trigger. TimeToCall v1.0.1 has been submitted to the App Store for review.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*




