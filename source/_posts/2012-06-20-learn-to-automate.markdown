---
layout: post
title: "Learn to Automate"
date: 2012-06-20 08:57
comments: true
categories: 
---

It's been almost six months since the [Codecademy](http://www.codecademy.com) launched [learn to code in 2012](http://codeyear.com), headlined by [Mayor Bloomberg](https://twitter.com/mikebloomberg/status/154999795159805952). Lots of people pledged, lots signed up.

And I'll be flabbergasted if any of them are still doing it.

I'm not going to go into why having everybody learn to code is a bad thing in detail, Jeff Attwood nails that in [Please Don't Learn to Code](http://www.codinghorror.com/blog/2012/05/please-dont-learn-to-code.html). Short version, it puts the method before the problem, programmers like to solve problems and create solutions, and the tool they mostly use is code. We need problems solved and solutions, not more code.

But I was on a client site the other day and was shocked to see the amount of manual work performed by one member of the staff on their computer. Every day, without fail, they spend half an hour dragging and dropping files that are delivered electronically into one folder to other folders, where they are then used by other systems and staff. If they fail to drag and drop these files, the entire business process fails. If they are sick, no-one knows where each file needs to go, so this poor employee has to work every day to keep the business running (or login remotely).

I could not stand for this, I believe in the [Hiltmonism - Automate or Die!](http://hiltmon.com/blog/2011/12/04/hiltmonism-automate-or-die/). So I stepped in and wrote a few ruby scripts in a few minutes that are scheduled to run on his PC every day and do this work for him. The scripts are less than 10 LOC (lines of code) each, and Windows Scheduled Tasks takes care of the rest (this user just leaves his PC on). With a few lines of scripted code, I just saved this person hours of drudge a week and documented where each file needs to go in code. And they can go on vacation knowing the work will still get done.

Wouldn't it be nice if this user could create their own automations? If they could do this themselves. If they learned to code, they probably could do it. If they could even identify the problem and formulate a solution. If they could then logically write the script. If they could test it and set it up as a scheduled task. If, if, if!

But coding is too hard. Critical problem solving is hard. Logic is hard. Applying process is hard. Just getting something done is easy. And probably provides some kind of comfort and job security.

Maybe something like Apple's [Automator](http://support.apple.com/kb/HT2488?viewlocale=en_US&locale=en_US) would work for this person. It's a great idea, a visual way to script, but it's not available on Windows. And most users don't know that this exists anyway.

So, instead of using your geek friends to fix your printer or tell you what next PC to buy (which is why they hate you), pay them a few hours to watch you at work. Give them a problem to solve, what can be automated in your job. That's why we are programmers, we love the challenge of solving real world problems. We may find nothing, we may be able to script a portion of it quickly, or we may need more time to create a full-blown application. You have nothing to lose by seeing if some of your work can be automated, but man-years of your life to get back if some of it can.

There is no need to learn to code, but there is a need to automate. Either learn how to do that yourself, or hire someone to make it happen. Automation scripts are easy for us geeks to write, they are reliable, flexible, cheap, document institutional knowledge, and free people up to work on what they should be working on. And they do what computers are good at, drudge work without complaints or sick days.
