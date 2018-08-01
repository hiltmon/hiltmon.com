---
layout: post
title: "Notification City"
date: 2017-03-12 12:11:29 -0400
comments: true
categories: 
---

**It is best for your technology stack to tell you what went wrong as soon as it goes wrong to get the right level of attention in the correct timespan.**

I run a massive technology stack at work, filled up with multiple servers, plenty of web applications, loads of C++ programs and massive numbers of scheduled and recurring tasks, and I do it with an insanely tiny team and no [DevOps](https://en.wikipedia.org/wiki/DevOps) folks. Almost all of the time, our software works as designed and the entire network of systems runs just fine. Just like yours.

When systems fail, we get notified.

Depending on the nature of the failure, we get notified in different ways. This helps us quickly decide whether we need to stop what we are doing and react, or wait to see if more notifications follow.

And it works.

In this post, I will stay out of the technology and explain our thinking and implementation of notifications, how we send them, monitor them, use them and manage the volume so we are not, in any way, overloaded or subject to unnecessary noise.

### Crashes and Notifications

As an intentional design decision, my team writes software that intentionally crashes when things are not right. We do not catch and recover from exceptions, we crash. We wrap database changes in transactions so the crash is safe. We do not, under any circumstances, run systems that continuously and expectedly fail and quietly self-restart.

We rely on notifications to quickly tell us of the crash so we can see what went wrong and rectify the issue. We ensure, where possible, that our error messages are both clear and identify where the crash happened.

This design is justified as our systems are a network of interdependencies, and so a failure in one process over here can impact, or require reruns, over there. Since we are a small team, building a DevOps infrastructure to map and auto-recover on all of these paths, which are constantly changing, is not optimal. We'd spend all our time doing it.

And so we do it simply. Almost all our processes are launched from simple shell wrappers or `rake` tasks. When an execution fails, the shell wrapper captures the error, and fires off the appropriate notification to the appropriate channel, then logs it and pops it in the right chat room.

<span class="light">Aside: This works because we also design all our processes to carry on where they left off, so even the most critical real-time systems just carry on from where they left off on a restart after a crash. How we do that could fill a bunch of posts.</span>

### Errors and Failures

No matter how good your software quality, things will go wrong. Programmers introduce bugs, bad data causes failures, hardware fails, and external systems are not always there. Some of these issues are easily dealt with, the rest need human intervention.

For example, a large proportion of our software gets data from a remote location, munges it and bungs it into the database (or the other way around). More often that not, that data is remote and third-party. And reasonably frequently, their server is down, their data is late, or the data is bad.

Of course our code "attack dials" when servers are unavailable or data is not present, so we do not get notified of these events — that would flood us with useless notifications. But, if the process has been dialing a while, or the data is not available in the dial window, then we get a notification. And if the data is bad, the program that munges it will crash, sending a notification.

Processes that depend on this data do *not* notify that the data is missing.

Why not?

We already *know* that the data is missing from the first notification, no need to pile on more notifications saying the same thing. Their failures are also logged, but in a different location and chat room from the primary. This model helps recovery and reduces confusion in identification.

<span class="light">Aside: We also have a Wiki that tracks data dependencies, so we know which processes to rerun after we correct a failure. This wiki lists all the commands to paste, so its easy. Whenever we face a new situation, we update the wiki.</span>

### Success and Last Runs

Clearly we do not want a notification when an expected process runs successfully, that would create an insane flood of notifications. We still send them, with some third party software we cannot stop them, just to a different destination. These notifications are saved so we can review them if we want, but it does not alert the team.

Note that failures are also saved, so we can go back and see where and when what fails more often.

### Live Process Monitor

Real-time C++ programs are more difficult to manage. We write them as "bullet-proof" as possible, but they too can and are expected by design to fail. Known bad data situations are dealt with, but we want unusual situations to take them down.

For these, we, the humans, need to drop everything and act. For this we run a mix of open-source and our own home grown process monitors. As soon as a monitored program fails, we get a notification on a bunch of channels:

- Our [Sonya](https://en.wikipedia.org/wiki/Bitching_Betty), an electronic voice on an ancient Mac Pro, loudly tells us what failed. Having a "Bitching Betty" voice state the nature of the problem really gets our attention.  <span class="light">Aside: Sonya as in "get<strong>s on ya</strong> nerves", thanks British Rail.</span>
- We get an iMessage, on our phones and watches, for when we cannot hear Sonya.
- The error Notification Center chat room gets a message as well, which pops up a UI alert.

The live process monitor also watches our "Coal-mine Canary" processes. There are a few threads we run that crash early and quickly when things go wrong, oftentimes quickly enough for us to be on it when the important stuff gets ready to fail. These also get the Sonya alerts.

For example, we have a process called "universe" that runs all day long and it depends on a large number of our systems and services, so it's the first to die when things go wrong, a perfect "Coal-mine Canary" candidate. When Sonya squawks that "The universe has collapsed", we know bad things have happened.

### Ongoing Notifications

If we see the same notification and deal with the same interruption over and over again, then we know we have an ongoing problem. In this case, we stop all work and get it resolved. The cost in time and lost productivity of dealing with the same issue over and over again is not worth it. Especially in a small team of developers. Taking the time to get it fixed is always worth it.

To be clear, we do not muffle notifications and silently restart "known" failures. We fix them, over and above all other work. Silence means all is well, not "all is well except for the known failures".

It also ensures that when we do get a notification, we cannot and do not ignore it. The notification signals a real issue. We have no reason to tune out notifications, and therefore no reason to start ignoring them.

### Regular System and IT Activities

Of course, being a "normal" tech team, we also leverage the notification infrastructure for regular, non-failure mode notifications. We just send these to a system that logs them, a system we can glance at when we need to see what happened. These notifications are not sent to us humans in the regular chat rooms, so do not bother us. This includes:

- Hardware monitors reporting successful checks
- Runs that succeeded
- Programmer commits
- System deploys
- Software updates

### Notification Volume Management

Most notification systems projectile vomit notifications, they are as chatty as a flock of seagulls over a bag of chips or a lawyer in court. The negative is that no-one can deal with the noise and yet still spot the real issue, and eventually they tune the noise out.

So how do we manage the flood of notifications, keep them to a manageable trickle of things we need to respond to?

- Rule number one, we do not notify humans for informational purposes or success. That is all noise and we so not send these out, only log them. If the notice is expected or does not require immediate human response, do not send it to people, just save it.
- Use different channels for different importances. If immediate attention is needed, set off Sonya and the iMessage alerts. If not, send it to the monitored chat room to be dealt with later. And if no response is needed, log only.
- Notify once and once only, flooding the chat room with a bunch of notifications that were triggered by a single failure also adds noise and makes it harder to find what cause the cascade. Trust the humans to know what needs to be done to recover from an event.
- Get an intelligent repeating voice alert, like our Sonya, on the job for systems that must be up to transact business and keep her repeating the issue every few seconds until the system is back up. Its noisy and annoying, but others can hear when things are wrong and when they get back to normal. Oh, and do not send these notification by the normal channels, so they do not fill up your chat rooms.
- Use a chat room for failure notifications. Firstly, you can get alerts when new messages come in, but more importantly, the responder can identify which notifications have been dealt with by responding to the messages. So, if more than one person is looking, that chat room will tell them which ones have been dealt with, and by whom. That way, not everyone gets involved when an alert comes in. It also allows us to scroll back to see common failures and note what was done to rectify.

### Notification City

In our Notification City:

- When Sonya starts talking and our iMessages start pinging, we jump. She tells us which real-time system has failed and we go and see why, fix it and restart.
- When the "Coal-mine Canary" processes fail, Sonya and iMessage let us know as well. We look at the chat room to see what dependency triggered it.
- When a regular thread fails, it gets posted to the chat room, and we get a UI notification that it happened. We can then see what went wrong, make the necessary calls, get it going again, run the additional processes to recover and respond that the issue was resolved.
- When all goes well, we get no notifications at all, nothing in the chat room and no interruptions, and we can focus on our work. Later on, we can look at the logs and status screens to see all was well.

This allows us to focus on what we need to do, yet respond appropriately when notified. We're not inundated with noise or unnecessary messages, so we do not need to tune them out.

When we hear or get a notification, we know that the situation is exceptional, and, depending on the channel, we know whether to jump now or have a few minutes to respond.

**Our Sonya has been quiet today, all is well.**

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*