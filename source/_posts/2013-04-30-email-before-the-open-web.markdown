---
layout: post
title: "Email before the Open Web"
date: 2013-04-30 09:09
comments: true
categories: 
---

*Today, April 30, 2013 is the 20th anniversary of CERN making the WWW free, see [Twenty Years of a free, open web][1]. I thought I'd share a story about how it was like before then.*

The year was 1988 or 1989, and my Computer Science Professor wanted to send his first email. But first we had to connect our University to the fledgling Internet. Since I ran the UNIX lab, I was tasked to set this up.

{% img right /images/UCT.png 150 152 %}

I should point out that I was at the [University of Cape Town][2] in South Africa at the time, about as far from the physical internet as was possible back then.

This was before ISP's. We ran our own wires, hubs and routers. And the Computer Science department had it's own LAN. We also had a bank of modems available for graduate students to dial in from other parts of the campus. We were not even wired to the next building. That was our entire network.

Since we were not interconnected, we had no access to the fledgling DNS network that was growing in the United States. And web servers and web browsers had yet to leave the lab and be opened up. And SMTP, which the planetary email network still depends on, would only work in a fully-connected environment.

The first step was then to find a way to connect to this Internet thingie from the far end of the world.

{% img right /images/cambridge.png 150 189 %}

One of my Professor's colleagues had written in a letter that his University, The [University of Cambridge][3] in the UK, had already been connected, and offered to enable us to route through them. All we needed to do was find a way to connect to them first.

We could have just used one of our modems to call out to Cambridge via the phone network. But international phone calls to host slow modem connections were prohibitively expensive, and the international lines out of Africa were notoriously noisy and unreliable. We needed another way.

{% img right /images/rhodes.png 150 213 %}

Then we found out that the [Rhodes University][4] in Grahamstown in the Eastern Cape had been given a huge grant to pay for their connection to Cambridge. So my Professor got on the phone to his counterpart there and they agreed that UCT could route through Rhodes and piggyback on their UK connection.

So I set up a modem, scripts and routes to use UUCP (UNIX to UNIX copy) to connect our primary UNIX computer to the Rhodes one. It would dial up Rhodes every hour and use [UUCP][5] to transfer any files and messages between the two computers. I tested it by sending messages and files to my counterpart there. It was then up to the Rhodes computer to process any email messages for us.

And it worked. My Professor sat at my desk, typed in his email and hit send. Then we both stared at the screen. *Because nothing happened.* I checked the UUCP folders, and the message was there in the queue.  Sometime in the next hour, our modem awoke, called Rhodes and UUCP sent the message out. Rhodes forwarded it on sometime later to Cambridge and I have no idea how it went from there onwards.

The next morning we came in to see if there was a reply. But there was none. The UUCP queues and folders were empty. Maybe the message did not get through.

But the day after there was a message. It had come back through this ad-hoc network of computers, dial up connections, hand-coded scripts and home grown routing tables from the other end of the world.

[Donald Knuth][6] himself had replied to my Professor's first emailed question.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[1]:	http://info.cern.ch
[2]:	http://www.uct.ac.za
[3]:	http://www.cam.ac.uk
[4]:	http://www.ru.ac.za
[5]:	http://en.wikipedia.org/wiki/UUCP
[6]:	http://en.wikipedia.org/wiki/Donald_Knuth