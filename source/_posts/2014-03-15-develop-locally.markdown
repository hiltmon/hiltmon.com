---
layout: post
title: "Develop Locally, Stage Nearby, Production Anywhere"
date: 2014-03-15 13:12:08 -0400
comments: true
categories: 
---

One of the things that surprised me as I moved back into the land of corporate software is the number of developers I talk to that commute and work in offices **and yet develop on remote computers**. I thought, as you probably do, that by now *all* software development would be local, as in on the developer's own computer. 

Instead, it is not uncommon for corporate developers to rely on remote shells or desktop virtualization to access remote development computers and use them to code. It's slow, unproductive, frustrating and so pre-1990's.

*Aside: Back then, remote development was the norm. Mainframes were too expensive to give to developers and most production platforms were not available in desktop form. You had to develop remotely.*

In this post, I want to point out how delusional remote development is in the 21<sup>st</sup> century and how local development can meet all Corporate needs.

## The Remote Development Delusion

There are several reasons given by Corporates for this old-school behavior, all of which are bogus.

> bo·gus ˈbōgəs/ adjective  
> 1. not genuine or true; fake.

* **Security and Access Control**: The argument is that companies want to be sure that their developers do not run off with their source code, or that nothing is lost when computers get stolen or lost, that only authorized developers access the right parts of the code and that they can track who did what.

	Bogus because the average developer can still copy the code, or even rewrite it from scratch. Modern source code control systems and good network access control will resolve any security concern. Encrypted hard drives and startup passwords secure computers, even after theft.
* **Big or Sensitive Data**: The argument is that the amount of data processed by developers is huge, or the data itself is so sensitive, that they need to develop close to the data.
	
	Bogus because networks are plenty fast, developer databases do not need to be that huge and storage is cheap, so making local (or nearby) copies of data is simple. Bogus because sensitive data can be changed via scripts, or fake data generated.
* **Cost Savings**: The argument is that companies can share development resources such as licenses and installations and can therefore purchase cheaper computers for their developers.

	Bogus because the productivity losses in remote development by far outweigh the cost of a few measly licenses or computers. If a company cannot afford its development tools, it should not be using them. And developer tools these days are cheap or free, as are powerful computers, *and are licensed for local development*.
* **It's Policy**: The argument is that the company has a policy of remote development.

	*Bogus because the policy argument is always bogus*. Policies are made-up rules created by business people who generally know nothing about reality, or were written so long ago that no-one has cared to change them. Staff are forced to follow these bogus policies or be fired. It has nothing to do with right, productivity, cost or any other reality.

In each case, the argument put forward for remote development is bogus. Development on remote computers is slow, unproductive, subject to outages, and guaranteed to frustrate good developers and encourage them to leave.

## The Local Development Model

The local development model's mantra is simple, to:

> 1. Develop Locally  
> 2. Stage Nearby  
> 3. Production Anywhere  

Developers code and compile on their own computers, using locally installed tools. All projects are staged (and continuously integrated) on servers nearby (as in the same office or on the same network). And then code can be deployed anywhere to run in production.

It's simple, local development makes sense and is the most productive way to develop.

* It's responsive, developers press a key and the response is instant.
* Developers can work anywhere, any time. Give a developer a laptop and they can work from home or at night.
* Developers can use their favorite tools and productivity enhancers to speed up development.
* Developers are only constrained by their own abilities, and not by the resources available on shared development machines, network flakiness or the slowness of remote operation.
* All development tools can and do run locally, and are designed  and licensed to do so. Local development is the *expected* model.

Staging nearby also makes sense.

* For large and complex code bases you can run continuous integration tools to build and report on errors far quicker than attempting production builds.
* You can use virtualization to spin up clean staging virtual machines on cheap retail hardware.
* If a developer does break something, it's close bye and easy to recover. And no other developers are affected.

Only production need be remote, and that can and usually is anywhere.

## Secure Local Development for Corporates

But corporates need their controls and security blankets. It turns out that the local development model can easily be made as secure and controlled as needed without punishing developers and throttling productivity.

Lets take each core remote development argument one at a time.

### Security and Access Control

Corporates want to be sure that the code and data is secure and only authorized personnel can access it. Easy:

* All modern computers and Operating Systems support encrypted hard drives. A password is needed to unlock the hard disk and yet another is needed to log in. A stolen encrypted hard drive is useless, and many systems can be remote wiped.
* All modern operating systems are built to keep folks out, and only to enable access by authorized users. Strong passwords are good enough, and even biometric access is available.
* If the data and access are secured, then communication needs to be as well. All systems come with built-in encrypted Virtual Private Networking to secure communications.
* Access to code can be controlled using an in-house hosted Source Code Control system. Developers can only see the projects that the company wants them to see, and the code is saved, logged, tracked and maintained in-house.

In short, no problem here.

### Big or Sensitive Data

Corporates argue that their data is too large, or is so sensitive that it needs to be tightly secured so development has to happen remotely. We've already covered securing code, the same applies to data, so what about data size? Well, assuming the developer needs access to *the whole* data set, easy:

* Modern hard drives are cheap and huge. And to be clear, there are exceptionally few corporate databases that cannot fit easily on a modern laptop drive. Big data is real, but rare. And even if the data is bigger than modern laptop drives, desktops with lots of drive bays or even SAN's are ridiculously cheap.
* If data is too sensitive, run a script on a copy of the database to remove or change sensitive information. For example, replace all credit card numbers with fake ones. Or use scripts to generate accurate yet fake data for developers. There are lots of tools out there to help do this.
* If the data is stored in a commercial database product, and the company is so cheap it does not buy licenses for developers, then maybe they cannot run it locally. Fine, but modern networks are fast, and running a one additional license as a development database server nearby, close to staging, accessible via VPN, is cheap.
* And if the company really wants to be tight, it can create and clone secure virtual machines that developers can spin up and run whenever they need data access.

It is rare that a developer needs access to the entirety of a database, and even rarer that the data does not fit on a local disk. Big data is not a problem. And there are solutions to sensitive data, so that too is not a problem.

### Cost Savings

But what about the cost of all these powerful laptops, tool licenses and staging servers? I could point out that maintaining development servers, licensing and the infrastructure to support remote development is just as high cost (oh, I just did). But:

* Computers are cheap, ridiculously so. And for the price you get lots of fast cores, oodles of RAM and massive hard disks. People and people's time is expensive. What would you rather spend money on?
* Modern development tools assume local development and so license terms and conditions expect this. The cost of giving each developer a licensed copy vs running a the same licensing centrally is exactly the same.
* And then there is the free and open source option. Instead of using expensive proprietary tools, try using open source languages that all the cool companies are using. The cost of getting support on Open Source is negligible and the products are being used by millions.

Choosing between needing more expensive developers using cheaper computers versus having fewer, more productive ones is easy when you look at the cost. Local development is cheaper.

### Policies

And then there is the legacy of policy. A business that is too rigid to change in the face of changing technologies, costs and realities has no right to survive. A business that is constrained by policy cannot evolve.

If a company wants to hang on to their developers, and get development done quicker and better, local development is the way to go. And if the only thing that's holding the company back is a few silly written rules, er policies, *burn them*.

## Develop Locally, Stage Nearby, Production Anywhere

Back in the 1970's, 1980's and early 1990's, remote development was the norm. Because it had to be. Mainframes and server platforms were expensive and unavailable on desktops. Computers were not secure and networks were unavailable or slow. And the tools were designed for this model.

The downsides were the same as modern remote development: key press delays, slowdowns as other users took too many resources, layers of security and technology needed to enable remote access and all sorts of flakiness and problems. The upside, well, it was the only way to develop.

But since then we've moved on. A computer on every desk (and now lap and pocket) is the norm. Servers and server platforms can run on laptops as well as on big iron in production. Computers are secure and fast, encrypted networking is ubiquitous.

There is no downside to local development. The last 20 years have been spent making local development a reality. The upside is huge. Faster, anytime, anywhere, productive developers result. 

There is no downside to nearby (or even local) staging. The upside is also huge. Better, faster builds, quicker identification of issues, and better testing all result.

Welcome to the 21<sup>st</sup> century. **Develop Locally, Stage Nearby, Production Anywhere.** Remote development's time has passed.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*