---
layout: post
title: "TimeToCall - The MacGuffin"
date: 2013-02-05 10:15
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 8** in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iPhone app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software. [Back to part 7]({{ root_url }}/blog/2013/02/04/timetocall-polishing-the-app/) or [start at part 1 first]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/).*

## The MacGuffin

Not all the work [Sweating the Details]({{ root_url }}/blog/2013/02/03/timetocall-sweating-the-details/) and [Polishing]({{ root_url }}/blog/2013/02/04/timetocall-polishing-the-app/) is about making things better, correct or even perfect. Sometimes it’s also about personality, giving the application some character, or throwing in a [MacGuffin](http://en.wikipedia.org/wiki/MacGuffin) or two, features that are expected, hidden on purpose, and not really needed. 

> The point of this post is to show that all software has features that user’s expect, demand and will most likely never ever use. But you still have to think about it, design it, program it, test it, sweat its details and polish it. It adds time and cost to the application, but just as the MacGuffin is a useless plot point that sets up a movie, so these features are needed to ‘complete’ the application, compete in the market on feature comparison lists, or just check the customer’s “I must have this” list.

The optimizer in [TimeToCall]({{ root_url }}/timetocall/) is my MacGuffin feature, it’s expected to be there, but not useful at all. The purpose of the app is to ‘play’ with time, *not solve it for you*. And an optimizer cannot really pick the best time anyway. So, instead of developing a cold, boring, and logically correct one, I intentionally developed and shipped a faulty, opinionated one. It does not crash, it just picks the wrong times with regularity.

## The Optimizer

As you by now know, the primary purpose of [TimeToCall]({{ root_url }}/timetocall/) is to help people figure out the best time to call other timezones such that all participants are involved at convenient time in their locations.

The user can figure this out by ‘playing’ with time to see when these moments occur.

The idea of an optimizer is to come up with the single best *Time to Call* given an arbitrary source and destination set. That would not work as the optimal time is somewhere within a *window* of time, from a certain hour to certain hour.

Instead, I decided to find the *earliest best time* and *latest best time* to call, the ends of the window. But I needed to set some constraints to ensure these times were ‘good’. I did not want the earliest calls to happen before 7AM as that’s just too early, nor did I want the latest calls to happen after 10PM. Constraints set.

The optimizer logic is simple. The earliest optimizer finds the location furthest west, bumps it to 7AM, adjusts the remaining times and presents that as the best early time to call. Actually, it adjusts the source time such that the westernmost location is at 7AM. Tap the `AM` button to see it in action.

The latest optimizer does the same with the easternmost location, bumps it to 10PM and calculates back. Tap the `PM` button to see it in action.

Not bad. But not good either.

It has three glaring faults. Do you see them?

1. It fails to optimize across the date line.
2. It still optimizes to ‘bad’ times
3. The edges of the ‘good’ window are generally the least-‘good’ *Times to Call*.

### Optimize across the date line

Try Los Angeles and Sydney and optimize. The `PM` optimizer picks Sydney at 10PM making LA 3AM, yet optimally 10AM in Sydney is a great time to call LA at 3PM.

This happens because the starting point of the optimizer is the east/west divide, or GMT. It goes west of GMT and east of GMT. It should, instead, use the ‘distance’ in hours from a calculated midpoint, not east and west. An optimizer like that would pick better call times for the example set.

But I chose not to implement it. I wanted a faulty optimizer. This is the app’s MacGuffin feature, it can’t work, and it’s not supposed to work.

### Optimized to ‘bad’ hours

Try Los Angeles, Sydney and London, hit `PM` and Los Angeles is in a  ‘bad’ time to call (Sydney gets 10PM, LA is 3AM).

So why the ‘bad’ time? The time excluded by the optimizer’s constraints is three hours *longer* than the ‘bad’ hours (see [Good and Bad Times to Call]({{ root_url }}/blog/2013/02/02/timetocall-good-and-bad-times-to-call/)). It means that there are sets of locations such as the above where at least one location will have a ‘bad’ time picked by the optimizer.

This issue is also easy to fix. I could adjust the optimizer’s constraints to be 6AM on the earliest and 12AM on the latest, and it would work much better (all ‘good’ times to call). But in reality, even though the hours are ‘good’, they are not the way people *normally* work and think. I tried the change, and it made the app feel soulless and mechanical. 

A faulty, or worse, optimizer just *felt* better. Then again, it is the MacGuffin feature.

### Optimize to the Edges

The earliest best time and the latest best time are both valid times for the optimizer, but are pretty useless to the user. Times somewhere *within* the time window are going to be much better. The question is *which time within the window is best?*

I don’t know.

It depends on the user’s schedule, the people they are calling’s schedules, the day of the week, differing office hours, meetings, commute times, habits, etc. It may even change from call to call as people’s lifestyles change. There is no way for this simple app to know.

I could have written the optimizer to pick the middle time in the window. One could argue that logically that’s the best *Time to Call* given no other knowledge. But that is Vulcan thinking, not human.

Since we do not know the people involved’s schedules, the optimizer can only be a MacGuffin feature.

## Shipping the Optimizer Issue

So I left the optimizer with its smaller constraint window, faulty starting point and edge seeker as is. But why?

One, it makes the application feel and work more naturally for the vast majority of timezones combinations, especially the closer ones. It only *screws up* when the locations are too far apart or there is nothing near GMT.

Secondly, the goal of the app is to enable the user to ‘play’ with time, **not solve it for them**. Moving the time slider up and down is interactive, fun and helps the user achieve their goal of choosing the best *Time to Call*. It really does not need an optimizer, but *should* have one, hence the MacGuffin.

Thirdly, I wanted my users to know they are smarter than the app. I hoped that my test users would *not* notice these intentional screw-ups. And I received no feedback on it during the beta. Instead, something amazing happened. My users gained a feeling of superiority, reward and achievement, because *they* could and did find a ‘better’ *Time to Call*  than the software.

Fourthly, users want a suitable *Time to Call* within the ‘good’ window, not at the edges that are found by a mechanical optimizer. So they ‘play’ with time to find it. And optimizer really does not help here, it gets in the way (even a perfectly correct one) and that is why I made accessing it less intuitive.

And finally, the optimizer cannot choose *suitable*. The best *Time to Call* from the user’s perspective is somewhere inside the ‘good’ window, but where inside that window is a *subjective* decision, a user decision. You can’t write an optimizer to pick the best subjective time for call without access to everyone’s schedules. Which makes this a truly MacGuffin-esque feature. But since it is expected, best to give it quirks and a personality.

Once the application is released and in the wild, I will continue to monitor. I’m treating the optimizer as this application’s [MacGuffin](http://en.wikipedia.org/wiki/MacGuffin) feature.  I expect this MacGuffin will forgotten as people ‘play’ with time. If I get feedback that the optimizer is useful and not a MacGuffin, and my users want a less faulty one (note I did not write ‘correct’ one), I will release it in an update. If I get no feedback at all, which I expect to be the case, I will leave it as is, or even remove it quietly later.

**Next:** [Part 9: Dawdle to the Finish]({{ root_url }}/blog/2013/02/06/timetocall-dawdle-to-the-finish/).

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
