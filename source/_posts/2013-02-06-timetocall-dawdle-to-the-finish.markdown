---
layout: post
title: "TimeToCall - Dawdle to the Finish"
date: 2013-02-06 10:28
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 9** in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iPhone app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software. [Back to part 8]({{ root_url }}/blog/2013/02/05/timetocall-the-macguffin/) or [start at part 1 first]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/).*

## Dawdle To the Finish

The end is in sight. But the light at the end of the tunnel is dim. There are many miles to go before [TimeToCall]({{ root_url }}/timetocall/) can ship. Enough bad clichés.

We all believe in a “sprint to the finish”, but the reality is it’s more a long, slow slog to the finish. You need to nail the last bugs and usability issues, and that means a Beta test. You need to prepare a lot of stuff for the App Store. You need to create the support web site and optionally, the app web site as well. And if you like, you can go all the way and make a press kit and marketing plan, but I’ll leave that out for now.

## Beta Testing

Up until now, the developer, and maybe a few friends and colleagues, have been the only people who have seen and touched the product. To paraphrase [Helmuth von Moltke the Elder](http://en.wikipedia.org/wiki/Helmuth_von_Moltke_the_Elder), **no application survives contact with real, live users**. You need to expand the testing group to a bunch of opinionated people outside your comfort zone. People with different experiences and expectations, people who would use your application, but maybe in ways you never dreamed of. And people who are not afraid to constructively criticize the app.

And honestly, as a developer, you don’t always see what you are missing. It’s why writers have editors, sports people have coaches, and I guess we all have parents.

[TimeToCall]({{ root_url }}/timetocall/) is a simple app, but I still ran a Beta test. It was short, just 2 weeks. In that time, I issued six releases. Yes, for a simple, 4-view app, there were a lot of changes. Many have been described in [Sweating the Details]({{ root_url }}/blog/2013/02/03/timetocall-sweating-the-details/) and [Polishing the App]({{ root_url }}/blog/2013/02/04/timetocall-polishing-the-app/), but here area few more ‘gotchas’ found:

* The ‘playing’ with time slider worked great on all hardware *except* the  original iPad. Somehow the clock animations were locking up the main thread and making the slider “sticky”. I dusted off my old iPad 1 to test. Yikes! It was worse than sticky, the slider was completely unresponsive. But I wanted iPad 1 users to be able to run the app. Since UI drawing on iOS *needs* to be on the main thread, I made it work by adding a delay in the animation start when the user finishes moving the slider, and I kill animation as soon as the slider is touched. It works better on the iPad 1, but feels worse on all other devices that can handle real-time updates.
* The app did not rotate on iOS 5.1 iPads (I disabled rotation on iPhones). Since all my usual devices are iOS 6.x, I had not noticed this. On the original iPad, no iOS 6.x, no rotation. Since I had developed this app using the iOS 6.x libraries, the calls to accept rotation had changed. So I added them in.
* Our Japanese users sometimes searched for places in English, but because I had *replaced* all English city names with their Japanese counterparts, it did not work. As a result of Beta feedback, I made both available.

To simplify the process of Beta testing, I used [TestFlight](https://testflightapp.com) *without* it’s API, just to create a team and share the updates with them. It sure made the process of distributing betas and getting feedback easier. Their API adds the ability to get analytics from within the app as well as crash reports back. I felt that this app was too simple to need that complexity, so I did not use the API this time.

I think that for bigger commercial-grade applications, I would use the paid [HockeyApp](http://hockeyapp.net) product for better production-level analytics and crash logs.

## Prepare for the App Store

You cannot ship an iOS app without setting it up on the App Store (unless you are a large corporation). And there is a lot of work to do there as well.

Firstly, you need to sign up for a $99 a year developer account to enable you to sign and ship software through it. You also need to issue the developer certificate, ad-hoc certificate (for Beta releases) and distribution certificate for the final release. And if you use iAd, in-app purchases or Game Center, you need to set those up as well. And you need to register the Beta user’s devices so that they can test the app.

Secondly, you also need to set up the application itself in the store too. Create the name, set the app id (needed for the certificates) and input the basic information, including:

* Choosing categories of the application, so people can browse to it
* Setting up keywords to help people search for it
* Providing contact information for reviewers
* Setting the age rating
* Picking a price for the app

Then you need a whole bunch of collateral to go with the app on the store, including:

* A massive 1024x1024 image for iTunes Artwork (and a 512x512 one too). Apple uses these in the store and, if you are lucky, in their marketing too.
* A textual description, “elevator pitch” or marketing blurb to describe the app to potential buyers.
* And a set of 3-5 screenshots for each of the iPhone, iPhone 5 and iPad in Retina resolutions to show the app off.

Seems reasonable, but you also need *for each localized language*:

* Another well phrased marketing blurb that expresses exactly what the app does in that language.
* Another set of 3-5 screenshots for each of the iPhone, iPhone 5 and iPad in Retina resolutions in that language.

Be sure that the tone and content of each blurb matches the tone expected by folks in that region. My slightly humorous English blurb does not work in the Japanese market where the customer prefers a more serious and detailed explanation of what the app does.

## Support On the Web

One thing you really do need on the App Store is a link to your support page. And, if you have a product marketing page, a link to that too.

One of the biggest problems in the App Store is that  our customers don’t really know about the support link. As a result, if there is anything wrong with the app, they write a scathing review and give it one star. And other potential customers see the low star count and scathing reviews and do not purchase the app. Many a great app has failed because the reviews were really support calls and customers did not hit the support link.

There is nothing you can do about this. *Except issue a new release*. Apple’s App Store by default only shows reviews for the *current* version of the app. And most people never look at the *all versions* reviews. Which means that, as a developer, you need to get ahead of your reviews if they are bad and get a new release out without the problems very quickly.

But more experienced users of your app, or of iPhones or software in general, will look for the support link. Not only do they expect to see it, but they also expect it to work. Create a page somewhere that enables users to email you or fill in a web form to tell you what they are thinking. And monitor that address. And always respond to a support message.

One thing that static screenshots do not do is show the user *how* the application works, just how pretty it is. It is therefore recommended that you create a product web page that contains more information about the app. The best thing you can do is to create a short video that shows people actually using the app in the real world. There have been many occasions where I have made my purchase decision based on the video alone.

For [TimeToCall]({{ root_url }}/timetocall/), I am running a “teaser” page until the app is released, at [{{ root_url }}/timetocall/]({{ root_url }}/timetocall/). As soon as it’s released, I intend to replace the “teaser” page with a video demo and a bunch more irreverent text. Lights. Camera. Action!

## Not a Sprint

The last few steps in the process of making an iOS app are basically paperwork, running the Beta test, setting up the store and setting up the web collateral. But they too need to be designed, planned, reviewed, checked for accuracy and correctness, and that too takes a lot of time that needs to be budgeted for.  Fortunately, much of this time can be spent while the Beta is in progress.

Remember this, a great app with a terrible blurb, no support and no web site, will not sell. Unfortunately, the reverse may be true too. You really do not want to put all that time and money into an app and not get the bugs squashed, app store interesting and support available.

With all these steps complete, are we finally going to ship? Find out in the final part tomorrow.

**Next:** [Part 10: Shipping]({{ root_url }}/blog/2013/02/07/timetocall-shipping/).

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
