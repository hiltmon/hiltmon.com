---
layout: post
title: "Dog with a Bone"
date: 2013-01-24 09:38
comments: true
categories: 
---

I think one thing that is unique about programmers is that we are tenacious about getting a problem solved. As tenacious as a dog with a bone to chew. It irks us when things are not perfect, but instead of ignoring it or putting up with it, we put in the time and effort to solve it. No matter how small the niggle.

Maybe it’s simply because we can. Or maybe we’re anal or crazy. Or maybe we have wolf genes.

I was thinking about this last night at 2AM after a marathon coding and testing session. It all came about because a client mentioned *in passing* that three memorial dates out of thousands in her copy of [Kifu](http://www.kifuapp.com) were missing. She assumed that there must have been bad data, and I should not worry about it.

Telling a programmer not to worry about something is like taking a bone away from a dog. It drives us crazy.

So I checked the data, the three people existed, had passed away many years ago, and their passing dates were good. And they did have memorial dates, just a month later, on the next page of the calendar. I could have stopped there, but the client had an expectation that was not being met, maybe, just maybe, there was an edge case here.

So I checked the web and found a reference implementation of religious to secular date conversions, put in these dates and it spat out dates a month earlier than mine. Thousands worked, these three were different. How? See, its fun to try to figure this out.

I spent the night revisiting the code and the conversion rules to find why these three dates were coming out wrong. Finally I found several new edge cases in lunar to secular calendar conversions involving anniversary date shifts on lunar leap years that are followed by lunar short years, and implemented them. Now the three dates came out right. But did I mess up the remaining thousands?

To check, I took it to the next level. I wrote a script to take every date in the past 100 years and test my conversion against the reference, just to be sure that my implementation matched. It ran and ran until 2AM. And finally, it ended. With no mismatches.

I cannot say whether being a perfectionist is a good or a bad thing in life, but it is a necessity when crafting great products. So if there is something in your code-base that irks you, go after it like a dog with a bone and work on it until it is done and done right.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*