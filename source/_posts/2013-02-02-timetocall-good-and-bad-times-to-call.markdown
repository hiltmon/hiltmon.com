---
layout: post
title: "TimeToCall - Good and Bad Times to Call"
date: 2013-02-02 11:38
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 5** in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iPhone app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software. [Back to part 4]({{ root_url }}/blog/2013/02/01/timetocall-presenting-the-clock/) or [start at part 1 first]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/).*

## Good and Bad Times to Call

The purpose of the [TimeToCall]({{ root_url }}/timetocall/) application is to help the user see what time it is in a set of destinations when they call from a source location **at a given time**. The primary interaction with the application is then for the user to ‘play’ with time to *find* the best, technically optimal, time for everyone.

I wanted to make it easy for the user to understand when were ‘good’ times at each destination and when were ‘bad’ times to call.

But when is ‘good’ and ‘bad’, and how to display it intuitively? These were the next design decisions.

## Defining ‘good’ and ‘bad’ times to call

I started by trying to determine ‘good’ times to call people. At first blush, standard working hours (9AM - 5PM) seem to be very ‘good’ times to call. But this window of time is too narrow, it’s only 8 hours out of 24. As a result, it’s not possible to overlap working hours with a location more than 8 hours away. I tried to expand this window by a few hours each way, but it remained too narrow.

So I went in the opposite direction, I tried to determine when is a ‘bad’ time to call? For me, it is when people are sleeping, say 10PM to 6AM. But that too is still an 8-hour window, and you still cannot to find overlaps with locations on the opposite side of the world. 

So I compromised. I chose 12AM (midnight) to 6AM as the ‘bad’ time. I believe people will generally not mind staying up late for a call, but hate to have their [REM sleep](http://en.wikipedia.org/wiki/Rapid_eye_movement_sleep) interrupted, or have to wake up too early for a call. And I’m old enough to still believe that the 12AM to 6AM calls are the scariest, because those are usually bad news calls.

## How to present ‘good’ and ‘bad’?

OK, so ‘good’ is after 6AM until midnight. That’s settled. Now how to present it? Some of my *silly* ideas included:

* Red and green traffic lights, red for ‘bad’, green for ‘good’, amber for iffy. But traffic lights are so 1980’s, hard for colorblind people to read, and are useless for VoiceOver.
* Ticks and crosses, tick is ‘good’. Symbols are easy to recognize, but they do not tell you how ‘good’ the time is. I mean, 11AM and 11PM are both ‘good’ times to call, but we all prefer to receive 11AM calls (they are ‘better’).
* Displaying a percentage ‘goodness’ was a silly idea, as what does 78% mean in terms of ‘goodness’ to call? Seriously though, I did take the time to calculate an Isosceles Trapezoid (or Trapezium) graph that went from 0% for ‘bad’ to 100% for ‘good’, with the 100% edge being working hours.
* And my next doozy of an idea was using bars like your phone shows signal strength. It looked great, but again, 3 vs 4 bars means exactly what?

So back to the question of ‘good’ times to call, how do we determine ‘better’ times within that period. Well, we could say that work hours (9AM - 5PM) are best, 6AM - 9AM are not as ‘good’ hours (wake up and commuting times), 5PM - 8PM is okay (but you may interrupt dinner) and 8PM to midnight is late but doable. Great, I had unintentionally broken the day into periods.

And the light went on.

{% img left /images/lightbulb.png 60 64 %}

**I realized that by *knowing* the period in the day, the user gets a better feel for the state of mind of people in that time zone**. In the early morning, you can expect people to be dopey; during the day, busy; evenings socializing or late at night trying to settle down. I realized that this kind of information is great for the user of the app, and I wanted a way to show it.

And that is how I came up with the time period imagery for each time shown so you can get a feel for what is happening then. It enabled me to create, using color and art, a unique representation of each period, and to enhance it with words for non-seeing users.

The result was this, a color spectrum book-ended by night imagery, darker blue in the morning, orange sunset in the evening and bright, bright days:

{% img /images/timetocall-day-periods.jpg 685 66 %}

* **Midnight to 6AM**: Before Dawn, dark sky, stars, sleeping folks.
* **6AM to 9AM**: Breakfast, orange sun rising, coffee being brewed.
* **9AM to 12PM**: Morning, bright morning sun, blue skies, great time to call.
* **12PM to 3PM**: Lunch, brightest sun at its peak, may be interrupting lunch or siesta.
* **3PM to 6PM**: Afternoon, sun moving on, also a great time to call (so I made it a reflection of the morning image).
* **6PM to 9PM**: Dinner, reddish sun sets, people still awake, still okay to call.
* **9PM to Midnight**: Late at night, lights are on, folks chilling and getting ready for bed.

So, the design to help users to get a feel for when is a ‘good’ *Time to Call* while ‘playing’ with time is a combination of an [easy to read clock face]({{ root_url }}/blog/2013/02/01/timetocall-presenting-the-clock/) and bright, color shifting images. On top of that, the user can *at a glance* also estimate the ‘mood’ of people in each place. Lovely.

**Next:** [Part 6: Sweating the Details]({{ root_url }}/blog/2013/02/03/timetocall-sweating-the-details/).

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
