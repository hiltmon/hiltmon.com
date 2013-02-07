---
layout: post
title: "TimeToCall - Shipping"
date: 2013-02-07 08:18
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 10**, the **last** part in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iOS app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software. [Back to part 9]({{ root_url }}/blog/2013/02/06/timetocall-dawdle-to-the-finish/) or [start at part 1 first]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/).*

## Is It Ready to Ship?

Probably the hardest part of the process to craft a quality application is to decide *when* to ship it. This is because there exists a tradeoff between whether to ship the application with its current feature set or whether to delay shipping to add new features.

In a way, the decision is easy:

{% blockquote %}
Good developers develop,
Great developers ship.
{% endblockquote %}

But most developers have a hard time getting there. 

## Why would it *not* be ready to ship?

I mean, you’ve gone through all the time, effort and cost ([part 1]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/)) to design, build ([part 2]({{ root_url }}/blog/2013/01/30/timetocall-building-the-core/)), think through ([part 3]({{ root_url }}/blog/2013/01/31/timetocall-the-biggest-design-decision/), [part 4]({{ root_url }}/blog/2013/02/01/timetocall-presenting-the-clock/), [part 5]({{ root_url }}/blog/2013/02/02/timetocall-good-and-bad-times-to-call/)), sweat the details ([part 6]({{ root_url }}/blog/2013/02/03/timetocall-sweating-the-details/)), polish it ([part 7]({{ root_url }}/blog/2013/02/04/timetocall-polishing-the-app/)), add some MacGuffin features ([part 8]({{ root_url }}/blog/2013/02/05/timetocall-the-macguffin/)), beta test it, set it up on the app store and create the collateral ([part 9]({{ root_url }}/blog/2013/02/06/timetocall-dawdle-to-the-finish/)). What could possibly be the holdup?

The most common reasons are *shipping fear* and *feature creep*.

### Shipping Fear

Up until now, only a handful of your peers have seen and used the app. They have been supportive, helped you test and provided constructive criticism. You have been living and working in a bubble.

But now it’s time for the app to leave the nest.

And we developers worry. What if there are bugs we don’t know about? What if the public does not like it? What if the data in it is wrong? What if there is a better product out there? What if the Apple reviewer rejects it? What if we get sued by a patent troll? What if we did all of this and it does not sell any? What it it crashes on everyone else’s device? What if they *hate* it?

Shipping fear affects all developers, we are perfectionists and we never believe our own products are finished or even good enough to go out the door. We need to face our fear and know that we can, and will, correct anything that got past our eagle eyes and the brutal test by our Beta users. We can always issue an update.

Or recite the Dune Litany of Fear to get through it:

{% blockquote %}
I will not fear.
Fear is the mind-killer.
I will face my fear.
I will let it pass through me.
Where the fear has gone,
there shall be nothing.
Only I will remain.
{% endblockquote %}

### Feature Creep

This reason delays more shipping than anything else. We decide to add *just one more* feature before shipping, and then another. Oh, and this user *might* need another MacGuffin feature so we’d better add that, too.

Or we see a competitor product has a feature that we lack, and feel that we *need* to have it in order to compete. We *fear* the feature comparison.

What we forget is that we’ve already chosen the initial release feature set, made it great and are ready to ship. If the missing feature is real and not a MacGuffin, we’ll hear the need loud and clear from potential customers and can add it in the next release. There is no point adding features that real users do not need, just to make someone happy or cross an item of someone else’s checklist.

There is a huge list of features that *could* be added to [TimeToCall]({{ root_url }}/timetocall/), some my ideas, some from my Beta testers. These include:

* Adding dates to a [TimeToCall]({{ root_url }}/timetocall/) so you can set reminders in your calendar.
* iCloud sync between devices so all your installs of [TimeToCall]({{ root_url }}/timetocall/) have the same data.
* Weekly alerts when a call time comes up using built-in notifications.
* Call or meeting durations to ensure that the *end* of the call does not fall into a ‘bad’ time.
* Add phone numbers to calls so the user can just tap a phone number at the *Time to Call* to make the call.
* Add attendee names to each location in the *Time to Call* so you know who is where.
* Pop up an alert when daylight savings changes in a *Time to Call* so users know to ’play’ again to find a new optimal time.
* Create a ‘floating’ location that uses the GPS as source for all calls, with a reminder to ‘play’ with time each time the ‘floating’ location changes.
* Add a view in the App to market me and my company so I get more business

But I have added none of these.

## Yes It Is Ready!

At some point, the product needs to ship. To repeat, *the key is to find the minimal feature set to ship at version 1.0, and then add additional features afterwards*. 

This does mean that the product may be missing significant functionality on initial shipping compared to its competitors. As a developer, you need the confidence and the courage to ship and *know* that you can add features later. As a client, you need the app out there to help you get things done. Both parties need to get over shipping fear. Stand up, put your shoulders back, raise your chin, bring up your best steely gaze, recite the *Litany of Fear* and ship. 

You and the client will then need the thick skins to deal with people who will tell you that they will *not* purchase your product because something is missing, or its too expensive, or there is something wrong with how you do things. But you have to get it out there for this conversation to even start.

And all that criticism is actually not a bad thing. The more folks complaining that something is wrong or missing, the more you get feedback on what to work on next. It does not mean you have to do what they want, but if their need happens to be on your to do list, you surely can use their commentary to re-prioritize.

At the end of the day, you cannot sell the product and start to earn the return on your investment unless you ship. You cannot build a buzz or market your or your client’s services until you ship. The effort is done, the cost spent, so ship it, start earning the return, start supporting real paying customers, start the conversation in public, and start working on the next features to ship.

**I shipped [TimeToCall]({{ root_url }}/timetocall/). You can buy it in the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8).**

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
