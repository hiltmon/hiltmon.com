---
layout: post
title: "How I use OS X Tools to build a Linux-only Product"
date: 2014-03-27 20:43:24 -0400
comments: true
categories: 
---

{% img right /images/osx-mavericks-100px.png 100 91 %}

OS X really is a developer's dream platform, a solid UNIX core on which *almost* everything compiles with a brilliant graphical environment hosting the most amazing developer tools.

**It's the "*almost*" in the above sentence that has recently tripped me up.**

I have a new vendor library that does not compile or run on OS X (yet!). As this is a big project which I will be working on for months, I want to set up my development environment so that I am comfortable and productive.

{% img right /images/tux-100px.png 100 117 %}

The simple solution is to spin up a Linux VM with a GUI or a set of `vim` shells, and code away. With this simple solution I can tune the environment to match production, compile and build the product using this vendor library and know that it works.

But to use this simple solution, I need to learn different keyboard shortcuts, copy and paste are weird, there's no integration with my current platform, and the code is locked inside the VM. It violates my preferred [Develop Locally, Stage Nearby, Production Anywhere](http://hiltmon.com/blog/2014/03/15/develop-locally/) model. In short, doable but sufficiently different to make me pause.

{% pullquote %}
**{" The real issue here is not one of which platform is better or worse, the problem is *me*."}** I am working in parallel on a bunch of other OS X only projects using the same toolset in an environment that I have tuned and practiced on for years. Do I want to build the muscle memory and productivity tools on yet another platform, or can I somehow make the current set work? Can I deal with the frustration of having to switch working contexts, keyboard shortcuts and tools to do this? And do I have the time to set it up and develop the productivity mindset.
{% endpullquote %}

The answers are all **no**. I am building core product for a new business, I have deadlines and each hour I spend in setting up or learning a new platform is an hour *not* spent creating the products we need.

It would be much nicer if I could use my tried and true, native OS X tools and yet still compile and build this pure-Linux product.

So I found a way that works for me.

Sure its a case of a few hacks and hassles, but this is the *one and only* long term Linux project I have that is part of a lot of other OS X projects (many that deploy to Linux but can be developed locally).

My chosen solution is to do everything as usual on OS X, using the usual tools, local folders and standards, and run a micro-VM with mounted shared folders and `ssh` to handle the compile and run part (the one and only one thing I cannot do on OS X). I get all the productivity I am used to from OS X and its tools, and still build and run on a production-compatible system.

### In Summary

Here's how it works. Keep in mind that the source code is local, only compile and run happens on a local micro-VM:

* I launch [VMWare Fusion](http://www.vmware.com/products/fusion) which resumes the minimal [Centos 6.5](http://www.centos.org) VM that matches production (no GUI, minimal Linux install, nothing else running). Then hide it away.
* I use a shortcut key in [iTerm 2](http://hiltmon.com/blog/2013/02/13/make-iterm-2-more-mac-like/) to open a`ssh` session to this VM and use a `bash` alias to`cd` to the mounted, shared folder where the code on my computer can be found.
* I launch [Xcode](https://developer.apple.com/xcode/), open the project locally as usual, and start programming.
* I compile and build in the `ssh` terminal. *This is the only step different to all other projects.*
* I do everything else using local tools on OS X.

{% img /images/linux-only-1.png 681 439 %}

And I am maximally productive because I have not really had to change a thing about how I work.

### In Detail

The VM (called 'Witch') runs on my laptop's installation of VMWare Fusion. Since I use minimal Linux installs on our production servers, I did the same here. All I added were the `Developer Tools` and dependent libraries needed using the standard `yum` install process. And, of course, I copied over the vendor library and set up `ssh` access.

{% img right /images/linux-only-2.jpg 350 176 %}

The settings for the VM in VMware are such that networking is local to my laptop (nice and safe), and it mounts my shared folders automatically so it can get to the code. 

And that's the secret. *The VM "sees" the code as local to it while I see it as local to me.* 

{% img left /images/linux-only-3.jpg 375 100 %}

These shared folders can be found in `/mnt/hgfs` by default (you need to make sure VMWare tools are installed and running). 

I also set an alias in the VM's `.bash_profile` that enables me to `cd` to my project folder easily:

	alias cdsc='cd /mnt/hgfs/Projects/Client/ProjectName/'
	
In iTerm 2, I created a profile with a shortcut key (in this case `⌃⌘W` for "Witch") to launch an `ssh` terminal session to this VM using my preferred development login.

{% img /images/linux-only-4.png 678 410 %}

And finally, I created the Xcode project using my [Xcode and the Simple C++ Project Structure](http://hiltmon.com/blog/2013/07/05/xcode-and-the-simple-c-plus-plus-project-structure/) and [Xcode 4 Code Completion for External Build Projects](http://hiltmon.com/blog/2013/07/07/xcode-4-code-completion-for-external-build-projects/) standards.

Code in Xcode, `⌘⇥` to the shell to compile and run, `⌘⇥` back to code some more. *And if I use the Xcode compiler, well, linking fails as the vendor library is not compatible, but all the other IDE features work just fine so compilation errors are easy to detect.*

### Quick Start this Environment

Since I switch between many projects every day, I automated it such that I can get this environment up in seconds. When I want to work on this project, I:

* Launch VMWare using [Alfred](http://www.alfredapp.com), which resumes the VM automatically.
* Launch iTerm 2 (on my system that's `⌃⌘T`) then press `⌃⌘W` to open the SSH terminal in a tab. I then type `cdsc` to change to the project folder.
* Open Xcode, and off I go.

### Benefits

The benefits to me are manyfold:

* I get to use the tools I use on all other projects for this one, thereby maximizing my own productivity.
* I get to build and run the program in its natural environment so I know it will compile and run in production.
* It's all local, on my hard drive, accessible to all my tools which means I can work on this project anywhere, anytime on my laptop, and it gets backed up via Time Machine (and of course pushed to a `git` server).
* I do not have to remember which context or environment I am in and the keys and shortcuts that match, I simply remain in an OS X context.
* And *when* the vendor sends me an OS X version of the library, it will just work without me changing a thing. I will just have to press `⌘B` to build and run it from Xcode.

I think that I did this mainly because I do have so many other projects I work on every day in OS X. I did not want this one to be any different. Instead of learning something new or different, I chose to bend this project to my will. I think if I did more of these pure Linux projects, it would obviously be better to set up, configure and make productive a true Linux development environment. But I need to be writing code and shipping product not learning new things right now.

So I found a way to use my OS X tools and shortcuts and productivity aids to build a very native Linux-only product.

Maybe some of the ideas and tricks in this post can help you with your second platform development.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*