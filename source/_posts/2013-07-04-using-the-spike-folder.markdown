---
layout: post
title: "Using the Spike Folder"
date: 2013-07-04 17:48
comments: true
categories: [ programming, development ]
---

In yesterday's post [A Simple C++ Project Structure](http://www.hiltmon.com/blog/2013/07/03/a-simple-c-plus-plus-project-structure/), I mentioned the `spike` folder. In today's post, I'll write more about how I use it.

By the way, I have previously written about [spike solutions](http://www.hiltmon.com/blog/2012/04/06/spike-solutions/), wherein I create solutions for the bigger technical problems at the start of a project to be sure they are achievable. *This is different.*

In this case, being back in C++ and rusty as an old door hinge, I also needed to create and test out snippets of code I *could* be using without having to `make` and run the entire product. So I create spike `.cpp` files in the `spike` folder to try things out.

{% img right /images/code-runner.jpg 328 409 %}

But making and running these is such a pain. Instead, I use Nikolai Krill's absolutely brilliant [Code Runner](http://krillapps.com/coderunner/) ([App Store link](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fcoderunner%252Fid433335799%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30)) app.

Just choose your language, spin up some code and hit ⌘R to run it. Errors and output are displayed in the panel at the bottom. What I did not know until recently was that it also dealt with compiled languages, so I could use it for experimental C++ files. And so I did.

Another great feature is that you can customize the compile and runtime environment in [Code Runner](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fcoderunner%252Fid433335799%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30) which means you can link to external libraries in spikes without having to create a `Makefile` entry.

*[Code Runner](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fcoderunner%252Fid433335799%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30) is another of those well-done, well though out, single use applications that we all love.*

{% img right /images/small-textmate-runner.jpg 243 199 %}

For TextMate 2 users, you can do the same in TextMate 2. Just open a `.cpp` file that contains an `int main...` and hit ⌘R to run it. But it does not enable you to set parameters or compilation flags like [Code Runner](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fcoderunner%252Fid433335799%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30) does.

Nowadays, whenever I get stuck or need a scratchpad to see how to do things without affecting the application's code, I just spin up 
[Code Runner](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fcoderunner%252Fid433335799%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30). If the code is any good, I save these spike programs in the `spike` folder for later when I will need that working code.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*