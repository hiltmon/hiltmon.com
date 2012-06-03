---
layout: post
title: "The Last of the Workstations"
date: 2012-06-03 13:22
comments: true
categories: 
---

{% blockquote %}
I started this post a few days ago, before WWDC 2012, before Jim Dalrymple's famous 'No' to whether it will be discontinued (see <a href="http://www.marco.org/2012/05/30/amplified-9">Marco's note</a>), when I felt that Apple had finally given up on the Mac Pro. I'm posting it now because I really do love true workstation performance, and hope that the Mac Pro product line continues this tradition.
{% endblockquote %}

Is the current Mac Pro the last of the true workstations? I hope not. Apple has not updated this product line for years now, yet there is nothing else on the market today that provides the Mac Pro's badass performance and expandability in the true workstation space.

<!--more-->

Right now, I am writing this on a my 2008 8-core Mac Pro with 3Ghz CPU's, 32GB RAM and 2.5TB of storage. Sitting next to it is it's twin sister with 4.5TB storage running OS X Server that I acquired a few months ago to replace my old 2006 4-core, 16GB RAM, 2TB server (the 2006 will not run Mountain Lion when it comes out, and the twin is second-hand).

But these computers, as fast and as great as they are, are getting a tad long in the tooth. No thunderbolt, old graphics cards, spinning hard drives, and the CPU's are not as fast as the current crop in the *laptop* space. I'd like to update to a new workstation, but I hope my choices are not limited to the current, aging crop of Mac Pros.

## My definition of a workstation

Workstation class computers are computers designed specifically for high-end technical or scientific applications, intended for a *single user* to enable them to perform massive amounts of computations or process massive amounts of data.  In contrast, the traditional desktop computer is more focussed on running multiple, low compute intensive applications with limited resources.

You can tell them apart by how they are made and the operating systems they run. Workstation class computers have server-grade CPUs (usually with larger caches, more cores and better multiprocessing circuitry), more memory slots running faster RAM, server grade multi-channel backplanes, more reliable components, faster server-grade storage and cost a whole bunch more. They invariably run a variant of UNIX that is optimized for large memory, fast process switching and getting out of the way of running compute-intensive applications. 

Regular desktops use cheaper CPUs, lower-life disks, single channel backplanes and slower RAM, in order to make them vastly cheaper. They also run consumer-grade operating systems that are tuned to foreground application performance and are RAM limited.

## The history of the workstation

The workstation age began when mini-computers were downsized into the tower or pizza-box configuration we see today. Maybe it was the Xerox Alto, maybe the PDP-8, or the Apollo that was the first, but to me, the first true workstation was the Sun SPARC.

It had everything a workstation user would need - a blazingly fast RISC CPU, lots of disk and RAM, a high resolution screen, ethernet access and a brilliant UNIX operating system. Not only that, but these computers were optimized for vector mathematics, making compute intensive operations wicked fast compared the the slower Intel and Motorola pipelines of the time.

The other workstation line that had my attention were the Silicon Graphics computers, especially the MIPS RISC/IRIX versions. They installed top-of-the-line custom graphics hardware on top of a workstation chassis and pretty much launched the desktop 3D modeling, 3D animation and real-time visualization businesses. They also created OpenGL, workstation class graphics which we now run on our iPhones. Later on, they also expanded in the massively parallel market with their NUMA technology, creating workstations with supercomputer level processing power.

But somehow this class of computer has been in decline since the early 2000's. Sun's systems have been overtaken by fast Intel based desktops, SGI is out of business, and only one company still makes workstations.

It's NeXT Computer, currently known as Apple Inc. It's the Mac Pro.

## Who uses workstations

The finance industry went nuts buying Sun workstations to run their models, risk and real-time systems. The bio-tech industry use these to model proteins and the astronomers map the sky with these.

The movie and TV industries went and bought SGI workstations to create animated graphics. All the major network logo animations and news graphics in the 90's and 00's were made on SGI boxes.

Universities bought NeXT computers for research computation and networking.  And others used these to process everything from gene sequencing to predicting the paths of hurricanes.

All the research that led to supercomputer applications started on workstations, where researchers used subsets of the data to create the models that now run on supercomputers to predict weather, disease spreads and other massive computing tasks.

## A large PC is not a workstation

Desktops sold by HP and Dell as workstation grade are most certainly *not* workstations. They may have the bigger server CPUs, but run on cheap motherboards, with limited memory slots, desktop grade hard drives and run consumer-grade operating systems. I should know, I used to buy these for traders so that they could have more screens attached.

You cannot get the linear compute performance out of these that you can on a Mac Pro, nor the data throughput. I ran the entire US home loan market on a Mac Pro, could not do it on a similarly configured HP or Dell desktop (and yes, I could if I used one of their server models).

## The end of the workstation

So, if this class of computer is so amazingly useful, how come the Mac Pro could be the last? I think there are several reasons:

* IT departments have stepped in and moved the heavy computing from the workstation to the server. It's easier for them to scale and manage the massive computing needs themselves than to trust the people on the front desk. And they can control it better.
* Traditional desktop computers have become a lot cheaper and Moore's Law means that even desktop computers now run extremely fast CPU's, blurring the line between desktop and workstation. Therefore, it's a lot cheaper to get a bunch of these to do the work, instead of buying workstations to get it done faster. And in a throwaway society, it's a lot cheaper to replace a desktop when it's cheaper components fail than maintain a workstation.
* Fast networks, fast servers, scaleable infrastructure and modern compute software libraries has led to the ability to create and grow distributed computing networks that are massively faster and more reliable than the old workstation.

But this transition to servers and distributed computing has its down sides as well:

* You need more people and infrastructure to support workstation-level computing. You need an IT team, server racks, networking people and routers, and then more to manage the load and balancing of this infrastructure.
* Creating workstation-class applications has become an incredibly complex task. Instead of just writing a program that can use a lot of RAM and cores and gets on with it, you need to create software that runs on servers, on clients, that distributes work, that serializes data across networks, that replicates itself, that load balances and that handles networking and server failures. Writing a compute intensive application is hard, writing a distributed one is nigh on impossible for a single programmer.

## Are workstations still needed?

Are you kidding me? Of course they are still needed.

Researchers need access to massive computing to perform their research, and a workstation is perfect for them. They can load all their data and computations on a single box, program it easily and iterate and iterate on their models until they get it right. You cannot do this easily with distributed computing, and supercomputers are too expensive.

Finance people can run their own quantitative models to give them an edge in the market. If they wait for IT to develop the model, set up the server, Q&A it and deploy it, they'll miss the opportunity.

It's a lot cheaper to run to Mac Pro than a series of distributed computers for amateurs and pro photographers and videographers to perform their work flows. Products like Aperture, Lightroom, After Effects, Final Cut Pro, Motion and Compressor are designed to maximize performance for their users on workstation-grade computers.

And as a developer, the ability to compile and run my work using all cores and RAM means that I can focus more on my models and results instead of waiting for compilations and slow runs.

## Sad if this is the end

But if this is the last of the workstations, then it is a sad day indeed. We're all going to have to adjust to working around the limitations of desktop computing, the complexities of distributed computing or the time suck of relying on IT to get things done.

No longer will I have the thrill of watching my 8-cores max out while free RAM drops to zero as my Mac Pro models every single home loan payment in the US market while *testing* my code.

I love having this workstation power under my desk, and I *use* it all the time. I hope that Apple continues the Mac Pro as a workstation-class computer for a long long time.

{% blockquote Maverick and Goose, Top Gun %}
I have the need...
...the need for speed.
{% endblockquote %}
