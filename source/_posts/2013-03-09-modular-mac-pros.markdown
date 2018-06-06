---
layout: post
title: "Modular Mac Pros, the new Burroughs B20?"
date: 2013-03-09 15:06
comments: true
categories: [ Writing ]
---

I've been watching a conversation on APP.NET speculating about the next Mac Pro form factor, triggered by Dan Frakes's article [The time is (finally) right for a Mac minitower](http://www.macworld.com/article/2029740/the-time-is-finally-right-for-a-mac-minitower.html) in MacWorld. *All we know about it is that Tim Cook said they were coming*.

One of the speculative themes in the discussion is a "modular" Mac Pro, where adding CPU's, drives or expansion cards would be a simple case of stacking another module on and using [thunderbolt](http://en.wikipedia.org/wiki/Thunderbolt_(interface) to keep it all together:

{% blockquote Kevin Hoctor https://alpha.app.net/kevinhoctor/post/3682876#3682819 %}
I’m completely convinced that Apple is dropping the enormous Mac Pro tower this year and is coming out with a small modular “pro” Mac to replace it. I don’t need it, but I think many do: http://j.mp/WSBux3
{% endblockquote %}

This discussion reminded me of one of the first computers I ever used for work, the Burroughs B20 series, sold by Unisys. I started on a B24 and upgraded to a B26 later.

{% img /images/b20.jpg 700 280 %}

These were amazing in their day. Because components were expensive, you could 'build' your computer as your needs and budget changed. Each stack started with a CPU unit on the left, early models had a Intel 80186, going up to the 80306 in the B26. You then added a hard drive module (they called  them Winchester drives back then) and added a graphics module to enable I/O (different ones for green screen and basic color).

{% img right /images/b20-face.jpg 195 116 %}

Need more RAM? Plug in a memory expansion module.  Needed a floppy disk, stack on a drive module. Need *another* floppy, stack it on. Tape backup? Another module. Need to cluster computers, stack on a cluster module (think ethernet card). More hard disk, add a disk expansion module. On some desks in our office, these stacks used to span the entire desk.

One of the most amazing features of the [CTOS](http://en.wikipedia.org/wiki/Convergent_Technologies_Operating_System) operating system that B20 series ran was that it handled the addition of modules and capabilities automatically, although, if my recollection is correct, you needed to add or remove modules while powered off. Power on and it "found" and just used the new module. Maybe the B26 was the first "it just works" computer.

If the new Mac Pros turn out to be Mac Mini sized modules, that would be cool; and I think OS X could easily be extended to support modular expansions. Need more CPU's, stack on a CPU module. More disks, add another SSD module.

But the thing that made these CTOS systems really sing was their clustering capability. Admittedly, their COAX network connections were slow by today's standards, but we could distribute work around up to 25 CTOS workstations very easily.

These days, with thunderbolt speed, maybe the new Mac Pros could be a network of modules instead of a single computer. The CPUs could be clustered and the disks shared as if a NAS, so it looks like a network of computers internally; but externally it looks and operates like a single computer with a lot of resources.

Wouldn't that be fun.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
