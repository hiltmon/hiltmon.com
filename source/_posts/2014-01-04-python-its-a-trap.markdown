---
layout: post
title: "Python: It's a Trap"
date: 2014-01-04 14:38
comments: true
categories: 
---

<span class="light">TL;DR: Python is the best language for quantitative scripting (because of its libraries). But it's a trap. Almost all programmers and libraries require Python 2 when Python 3 is out and way better. **Choosing to use an old language for new project traps us into supporting old languages, libraries and platforms. And that's not smart.** The intent of this post is to point out this odd stagnation and encourage the migration and adoption of Python 3, or, as it has happened in the past, we'll have to look elsewhere for a solution.</span>

Over the past few weeks, I have been looking at switching to the [Python](http://www.python.org) programming language for quantitative analytics development at work. On the surface, Python looks perfect for this - it has the best quantitative libraries (e.g. [numpy](http://www.numpy.org), [scipy](http://www.scipy.org) and [pandas](http://pandas.pydata.org)), it is the language taught in finance schools and it is a beautiful, fast and reliable scripting language to work with.

{% blockquote Admiral Ackbar %}
It's a Trap!
{% endblockquote %}

In my research I felt there was something wrong with the picture I was seeing, something on the periphery in the corner of my eye. And then I saw it: The stats on **Python 2.7 usage and compatibility vs Python 3.3 usage and compatibility** make no sense.

As a non-pythonista, my expectation was that after *five* years, Python 3.x would be the *most* used and *most* compatible platform. After 5 years, all libraries should have moved over, all new code should be written in it, all new technologies compatible with it. The reality is that less than 2%[^1] of all work is done in Python 3 even after 5 years! Python 2 is still 98% of the game. WTF? 

That's where the trap lies.

An old language stagnates, increases support burden and cost, and slows growth. People sticking with old languages are forced to use old libraries, old tools and run on old platforms. The reason languages update is to make them better, faster and to eliminate bad language design decisions. Picking an *old* platform for a *new* project traps you into long term support and maintenance of that *old* platform. That's the trap.

{% blockquote Pythia %}
All this has happened before. All this will happen again.
{% endblockquote %}

We've been there before. Back in the early 2000's, I was a [Perl](http://www.perl.org) programmer. Perl was *the* scripting language at the time, the one with the best libraries (see [CPAN](http://www.cpan.org)), the one with the latest tools and the best compatibility. But as the naughts progressed, Perl started to stagnate as a language. First, they started talking about a non-compatible [Perl 6](http://perl6.org) *that never happened*, and then the community left for [Ruby](https://www.ruby-lang.org/en/) and Python because they *were* happening. Perl, it's ecosystem and its community stagnated. 10 years later, Perl 5 is still with us. But I believed then that sticking with Perl beyond the middle 2000's would have been a bad idea. And it was for those who stayed.

Back then, the Python 2 community and ecosystem was dynamic and growing, as was the Ruby one. Back then, I chose Ruby over Python by a hair, and it was a great decision *for me*. Since I started with Ruby, it has gone through three revisions ([1.8](https://www.ruby-lang.org/en/news/2013/06/30/we-retire-1-8-7/), 1.9 and now 2.0) and the libraries and community have grown with it. Even when an incompatible version, 1.9, came out, the speed at which the community adopted it was tremendous. Ruby 2.1 came out a few days ago and already way more than 2% of the community is using it.

Other languages too have gone through changes as significant as the Python 3 move over the same period. [C#](http://en.wikipedia.org/wiki/C_Sharp_(programming_language), one of the most popular corporate programming platforms, went from 2.0 to 3.0 to 3.5 to 4.0, all incompatible revisions, yet most new C# code requires 4.0. [C++](http://en.wikipedia.org/wiki/C%2B%2B) went to C++11 over this time and the most popular C++ compilers happily compile it.

On the other hand, other languages too have remained weirdly behind, just like Python 2. Java went to 7 but no-one seems to write for it. Oh, they all install Java 7 (in order to get rid of those infernal update dialogs) but still run 6 in production.

It is possible that the reason some languages stay behind and others grow is because of the way the change happened. Ruby, C# and C++ (Clang) all have compilers that not only point out the incompatibilities with old code, but have ways to fix them easily. Maybe the Java compiler and the Python one do not.

Or maybe the reason they stay behind is because they are too well embedded in corporate infrastructure and too much code has been written in them to make it viable to change. That sure explains Java and Python, but does not explain C#.

Or maybe it's because these languages are taught in schools and the education system is slow to adopt the new version. Or maybe the community around these languages is more conservative, with an "it ain't broke, don't fix it" kind of attitude. Or maybe it's just too popular.

I do not know *why* people have stuck with Python 2.

I *do* know that Python 3 has been out for five years and is about to go through its fourth revision. I *do* know that it improves the way the language works in a myriad of ways, removes some really bad stuff, is stable, mature and runs brilliantly. And yet it has not been adopted.

Since I do not know why *everyone* is still on Python 2, I cannot offer the right solution. Only some ideas:

- If the reason people still use Python 2 is the community, then the community should start 2014 by installing Python 3.3 and using that. Put pressure on the library developers to get their products up to speed.
- If the reason is because your distribution installs an old version, pressure your vendor to put the new version in as default.
- If the reason is legacy code, spend the time now to fix and upgrade. Or you will get deeper and deeper into the trap.
- And if the reason is the language provider, then python.org should stop supporting the Python 2 stream. It works for other languages and it will force all users to upgrade.

I still think Python is currently the best language for quantitive analytics and development of ideas, but it is also a trap. The trap being that we really need to use the old version to do what we need to be done. It's like requiring users to be running Windows XP when Windows 8 is out and mature. This trap is holding everyone back.

If the trap remains, and it seems to be the case, then me choosing Python 2 as our development and production platform for new projects is nuts. I can, and probably will choose Python 3.3 for now as numpy and pandas should work, but I worry that if I wish to use other libraries, they will remain incompatible. And rewrite in C++ for production to avoid the trap.

Unfortunately, no real alternative exists for quantitative *scripting*. R is way too slow, and few know MATLAB. Java and C++ are just too heavy and require too much effort.

Or, if someone could make a numpy and pandas for Ruby (or even Go or Javascript), I'd use that in a New York minute.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[^1]: "Looking at download statistics for the Python Package Index, we can see that Python 3 represents under 2% of package downloads. Worse still, almost no code is written for Python 3." in [About Python 3](http://alexgaynor.net/2013/dec/30/about-python-3/)