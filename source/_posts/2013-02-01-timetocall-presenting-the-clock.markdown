---
layout: post
title: "TimeToCall - Presenting the Clock"
date: 2013-02-01 10:22
comments: true
categories: [ TimeToCall]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 4** in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iPhone app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software. [Back to part 3]({{ root_url }}/blog/2013/01/31/timetocall-the-biggest-design-decision/) or [start at part 1 first]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/).*

## Presenting The Clock

The second biggest design decision in [TimeToCall]({{ root_url }}/timetocall/) had to be the clock and its face. The application is all about ‘playing’ with time and time is intuitively associated with clocks. 

And clocks are cool.

So, what kind of clock? 

Yes, friends, what follows is almost 1,000 words on choosing a best way to show time for a simple, 4 view app. As if humanity has not being doing this for thousands of years!

### Digital Media, Digital Clock?

Since a day is 24 hours long, and I wanted users to know when it was day or night elsewhere, I initially went with a digital clock face design. I liked the idea of big, fat LED-style numbers and a blinking colon so it looked like one of those cheap digital clocks you get in hotel rooms or on old VCR’s. I *thought* that 24-hour digital time would be easier to read at a glance.

But that idea died very quickly. 

The first problem is that *most* people still *talk* in AM and PM. Most countries have settled on the 24-hour time for official business, you can tell because your computer will show 24 hour time for your locality (except America, Canada and Australia, they still show as 12 hour time). All military, police and other official conversations are all 24 hour time worldwide, “I arrived at the scene at 14:53.”.  But most people still say “3 o’clock” instead of “fifteen hundred”. And most people still prefer to run their diaries and calendars in 12-hour time. A 24 hour digital clock is correct, but not very user friendly.

The second problem is that digital faces I started to draw looked terrible. Not the design or color, they were great, but in the app it looked like the time information was just being *repeated* for each destination. I am sure this is because my old eyes just struggled to see the time *differences* at a glance. It looked like one of those spreadsheets full of columns of numbers that we all glaze over. Not cool.

Not only that, I could not find a nice way to show the time changing when the user ‘plays’ with time. I tried flashing the time, annoying, I tried the airport departures-board style flip animation, but that was hard to follow, I even played around with a matrix-like transformation when time warped and changed. All awful. There was no feeling of *movement* in time.

Digital media, sure, digital time, no.

### So Analog It Is

So I switched to an analog clock display. Analog clocks are good because they are simple, easy-to-interpret displays of information and given that we are all so used to the form, easy to read the time at a glance. On experimentation, it turned out that a stack of clocks with different times were easier for my old eyes to differentiate. And then I could animate the hands when time changes, which makes clocks cool.

### AM/PM

*But there be dragons*. A day is 24 hours long, and an analog clock has only 12. Without context, how do you know when the analog clock is showing 3AM or 3PM? Think about it, normal clocks do not help, they require the viewer of the clock to be aware of their own time context in order to determine morning or night when reading a clock. I needed a solution where the user could see *at a glance* whether the time was AM or PM.

So I experimented there too.

Apple, in its clocks app, inverts the clock when its night time (6PM to 6AM). So I created a clock where the background was white during the day, gray in the morning and evening and dark at night. It was nice, especially when ‘playing’ with time as the backgrounds got accordingly lighter and darker. But the darker clocks were harder to read against the dark app background. And both 6AM and 6PM has the same gray. There had to be a better way.

{% img /images/timetocall-transitions.jpg 656 152 %}

I tried a version where a sun would rise and rotate around the face for day time and a moon for rise and fall at night, but that was confusing and garish. I tried a version where the backgrounds I use for indicating the period of the day (morning, dinnertime, etc) were placed behind the clock, but that made the hands harder to read. There had to be a better way.

So I settled on subtlety instead. I placed an AM and a PM on the face and made the active one red and the inactive one gray. Red AM, gray PM means morning, gray AM, red PM means afternoon. I found it easy to determine when the clock was showing AM or PM. And the hands never get confused and the clock faces still stand out on the screen. **But how would it work out there in the real world?** I tested the clock face on a few friends and they subliminally knew the AM or PM of the time without being aware of the AM/PM image switch. It worked.

{% img /images/timetocall-icon-320.jpg 320 320 %}

I now had a design *form* for the clock, but I was not done. The rest of the work involved choosing the face number font, setting font sizes, drawing the major and minor tick marks, picking the color scheme and creating the clock face style. I prefer a simple clock face, so that it would be both recognizable and easy to read. Yet I also wanted classic looking numbers and classic hands that would not confuse readers. So I went with a paper textured face, tiny bezel, black minor tick marks, the same red for major tick marks, and classic hands with transparency and a shadow so you can see the minute hand behind the hour hand. And then put my name on it for fun.

I think the clock face turned out well. It is easy to read, differentiate and animate. So well that I just had to use it for the app icon.

**Next:** [Part 5: Good and Bad Times to Call]({{ root_url }}/blog/2013/02/02/timetocall-good-and-bad-times-to-call/).

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
