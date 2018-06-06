---
layout: post
title: "TimeToCall - The Effort and the Return"
date: 2013-01-29 19:33
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 1** in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iPhone app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software.*

## The Application Scope

[TimeToCall]({{ root_url }}/timetocall/) is a very simple universal application that contains only four views. Users can create named *Times to Call* to figure out when it is best to call a set of foreign locations. For more about what the application does, see the [TimeToCall]({{ root_url }}/timetocall/) product page.

In order to achieve this limited scope, I constructed four views:

{% img /images/timetocall-controllers.jpg 738 310 %}

The first view, Master, is just a table view with rows for each *Time to Call*. The second view, Detail, displays all the information we have about a *Time to Call* and enables the user to ‘play’ with time, the primary action of the app. The third view, Edit, enables the user to change the *Time to Call’s* location, name and destination. And the final view, Picker, enables the user to browse or search for locations.

Behind that is a simple data model that stores an array of these *Time to Call* objects. And a data set of places and their timezones.

A simple scope. A simple implementation. How long do you think it would take to do it right?

## The Effort

In total, the application, from first blush to submission to the App store took about 100 hours.

Yes, **ONE HUNDRED HOURS**. I used a timer.

It involved designing, coding, creating artwork, iterating, animating, testing, and then doing that all again for the iPad. And then creating localizations and data files. And fixing bugs and performance problems. And polishing and beta testing.

Sounds like a lot.

*The reality is that these 100 hours are just the start for most applications*. Most are more complex, have more views, interact with servers and do more things.

Oh sure, you can cut the time down, by *not* doing a universal version, by *not* creating any animations, or by *not* polishing or testing. But if you want people to like, *nee* love, your app and use it and tell others, you really need to put the effort in.

Lets assume an hourly rate of US$150.00, then 100 hours means a $15,000.00 cost. That seems a lot for a simple app with only four views (and no bugs)! Dropping iPad will maybe save you $3,000.00. Adding features will just increase the time and cost.

**The effort shows that creating a polished iOS app is not a quick nor cheap option**. Even if the app is so simple.

## The Return

Creating the application is the investment, income from sales is the return.

I could put this app up on the store for free. After all, it’s my time, my design, my effort and if you ignore the opportunity cost, that makes it theoretically cost free. The return on investment of a free app is zero. There is none. You’re giving it away.

Free does work for some developers. They want this magical unicorn-like thing called exposure. Or they want bragging rights that they have a large number of users. But in reality, they need to support and update the free app *for free*. Or, like many, they either choose to ship and stop, or they run out of money and have to get a real job so they stop. No support, no love for their customers, no real way to build a business or a long term relationship. 

That is no good. There should be a return. Lets say I price the app at 99c a pop and we run a break-even analysis:

{% img /images/timetocall-breakeven.jpg 600 400 %}

I need to sell 21,429 copies of the app to get my investment back and not lose any money. Given that this is such a simple app, no other price point makes sense, so no need to test them too.

If I sell 30,000 copies, I earn $21,000, or a $6,000 profit. Sounds good. Or 40,000 copies is a $13,000 profit. Sounds better. With numbers like these, it is easy to get starry eyed and forget about rent, food and taxes.

**But what is the *probability* of actually getting these sales numbers?** Well, if you Google around, you’ll find an *old* study that shows more than half of the *paid* apps on the App Store sell less than 10,000 copies (after they took out outliers). You’ll also find lots of articles on the few outliers who did sell millions and how they are taking a growing lion’s share of revenue out of the App store. And then there are lots of articles containing total download figures that include the millions of free app downloads, so it sorta kinda seems all apps do well.

Within all that noise is this truth. **The *majority* of *paid* apps on the App Store don’t even get close to 5,000 units sold, never-mind the old study’s 10,000 figure**.  Which means the probability of [TimeToCall]({{ root_url }}/timetocall/) achieving *less than one third* of the sales needed to break even is above 60%. Economically, it’s almost guaranteed to be a disaster, a loss making exercise.

## My Expectations

I will sell the app for 99c, I will not give it away. I did spend 100 hours making it.

I expect to sell a couple of hundred units over the next few *months* as friends and family and some of my readers purchase the app.

I expect to leave the app on the store for at least a year, but do *not* expect to ever exceed the 5,000 unit mark (50% probability).

I intend to spend more time (and therefore increase the cost and break-even) by supporting the product, issuing bug fixes and adding features.

I do not expect to make a penny in profit off of this app, ever! The chances of getting to even 21,429 units sold is just far too low.

## So really, why do it then?

I wanted to do this for several reasons:

* I wanted to check and ensure that my project estimations were accurate. Normally when a client requests an estimate, I have *incomplete* information about the app’s feature set, so I estimate what I know, and add a ‘fudge’ factor for the unknowns. With this app, I knew the full feature set at the start and made an estimate. After creating the app, I realized there were tasks I did not usually include in the estimate and now understand why my estimates are all a tad short. A good learning experience and better for my clients.
* I needed to update my iOS skills after a year in Rails-land. The last few iOS apps I did were pre-retina, pre-blocks, pre-ARC, on old versions of iOS. I wanted to both learn the newer technologies and also get a feel for how much time they saved. Which is why this app uses Core Animation, ARC, blocks and all the new and cool iOS technologies I could squeeze into it.
* I needed an app on the App store for portfolio purposes. I had pulled my old apps over a year ago as they did not reflect my current skill-set. And they were not really selling anyway. But clients do ask if there is an app they can download to get a feel for what I can produce.
* I wanted a real-world but fenced application development process to write about. I feel that there really does need to be a documented real-world example that helps potential clients to understand all that goes in to an app and why it costs what it does and takes as long as it does.

**Next:** [Part 2: Building the Core]({{ root_url }}/blog/2013/01/30/timetocall-building-the-core/).

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
