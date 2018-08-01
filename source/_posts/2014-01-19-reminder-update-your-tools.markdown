---
layout: post
title: "Reminder: Update your Tools"
date: 2014-01-19 12:06:25 -0500
comments: true
categories: 
---

At the start of every new year, I spend a the time to update all my tools and recompile all my products with them. At the cost of a few hours (or at worst, days) work, I get rid of most the maintenance hassles I faced before I used to do this and gain the benefits of all the new features and performance from updated tools.

I understand that, for all of us, updating our tools is surprisingly hard. Things that used to work now fail, incompatibilities have to be addressed and it takes time, perceived as unproductive time, to do. And then there is the risk that updating production servers will cause downtime for no valid reason. It's easy to feel that we should wait for the next release, or when we have some mythical down-time, or when we're forced to do so as the versions of our tools become obsolete. And it's hard to justify updating tools when there's real work to be done and no *current* perceived benefit in changing tools.

On the other hand, updating our tools *now* means we get the performance and feature benefits of these new tools *now*. We get the incompatibilities from last year out of the way, meaning that the products we make with these tools can move forward more easily (we're less likely to get stuck with a version dependency). We get to use newer and better versions of our libraries. Our servers get updated, run better and require less maintenance. We get to learn and practice the updated tools ideas and technologies. And the start of the year is the best time to do this as it's one of the slowest business times.

For me, that's actually quite a lot of work, but so worth it. Amongst other things, I have:

- Upgraded to Ruby 2.1.0 as it's the latest and fastest.
- Moved our Python code to 3.3.
- Moved all our Rails applications to 4.0.2 as that is current.
- Updated to the latest SASS, Rake, Sinatra, Node.JS and other tools.
- Updated all my Homebrew installs (`brew upgrade`). This entailed a non-trivial upgrade of PostgreSQL from 9.1 to 9.2 (I had to export and import all my databases)
- Updated all my CentOS servers and their tools to the new PostgreSQL, Ruby and Rails.
- Moved all our Windows C++ and C# applications to Visual Studio 2010 from 2008 (we run one version behind on all Microsoft products - been burned before)
- Recompiled all our C++ projects using the latest `clang` and `gcc` on each platform.
- Updated all Objective-C applications to the latest Xcode and recompiled with ARC and the latest libraries.

What did I get out of all of this work? On the surface, nothing much. The same old applications doing the same old things. But each and every one of them is now ready to take advantage of *new* tools, *new* technologies and *new* features in 2014. And most seem to run just a little better and a little faster and use a tad less memory than before. And best of all I have peace of mind, I know there are no legacy dependencies that are holding me back.

There is no good time to do this, so do it now. Get it over with for the year. Update your tools now. Or you never will.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*