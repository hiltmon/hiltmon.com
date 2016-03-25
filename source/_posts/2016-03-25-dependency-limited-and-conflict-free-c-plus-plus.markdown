---
layout: post
title: "Dependency Limited and Conflict Free C++"
date: 2016-03-25 08:57:53 -0400
comments: true
categories: [ c++, development, programming ]
---

<span class="light">TL;DR: Beware of libraries you need to compile yourself and copy-pasted code, the performance, maintenance and other hellscapes you create are not worth it in the medium and long run:</span>

1. <span class="light">Do not use dependencies that have dependencies *that you have to compile*.</span>
2. <span class="light">Do not use libraries depended on by dependencies anywhere else.</span>
3. <span class="light">Solve your own problems and understand the solutions. Do not copy-paste from the web.</span>
4. <span class="light">Always write your own code where performance and maintenance is critical.</span>

<span class="light">This post specifically targets C++, but is really a general set of rules and advice. See [NPM & left-pad: Have We Forgotten How To Program?](http://www.haneycodes.net/npm-left-pad-have-we-forgotten-how-to-program/) for a NodeJS scenario that this would have prevented.</span>

I write a boatload of C++ code these days, developing on the Mac and deploying to Linux servers. All of it is *dependency limited and conflict free*. What does this mean? **It means that I never have to deal with multiple versions of dependency libraries or on dependencies that have their own conflicting dependencies**. At best, I code in straight-up C++11, use the STL and rely on vendor precompiled libraries that are dependency limited. The result is fast code that I and my team can read and maintain, deploy and run on all platforms with ease.

## Dependency and Conflict Hell

When I started writing these products, I went mad and using a ton of third-party libraries. The theory was that these libraries were out there, already written and tested, *everyone used them*,  and I could leverage them to short-cut my development time and effort.

And it worked.

For a very short while.

Within weeks of starting, I found one of the libraries I was using stopped compiling. It started throwing really odd errors, yet nothing had changed. It turns out that this library relied on code in an old version of another library that had been deprecated in later versions. I  had added another dependency that needed a newer version of the same dependent library, and all hell broke loose.

The UNIX operating system solves dependency hell by allowing you to link your library to specific versions of libraries, so I could link to, for example, Boost v1.30.1 for the first dependency and Boost 1.52.0 for the other dependency — as long as they were compiled into separate libraries! Which means maintaining two installs of Boost and two environments just to get my dependencies to compile. And if I add another dependency that say requires a third version of Boost, complexity increases.

There are many problems with this:

- **When it comes to design and architecture**, I need to split up my dependencies into separate libraries that compile with their own dependencies and then link to them in the main application, or use static linking which is not the preferred option.

- **When it comes to maintenance**, I need to document where each dependency is, where its used and somehow describe the [Gordian Knot](https://en.wikipedia.org/wiki/Gordian_Knot) to myself and my team for use in 6 months time without context.

- **When it comes to setting up a development environment**, I need to somehow save old versions of dependencies and make complex Makefile trees to generate the correct versioned libraries.

- **When it comes to compiling**, I have to compile a lot more components or use static linking to ensure that the right library is linked and the right functions called, increasing executable size, memory use and complexity.

- **And when it comes to deployment**, I have to build this hellish mess for each platform.

## Aside: Debugging and Maintenance Hell

Solving for the above takes time, it's not hard, and once it's been done, you could argue for smooth sailing. I expect this is how most teams do it.

Until something goes wrong and you start to debug. I don't know about your tools, but mine always seem to find the "Jump to Definition" code in the wrong version of the wrong dependency every time. Which means that trying to find where something fails becomes that much harder. Is the error in the dependency, the dependency version or in my code? Ouch.

Or until time passes, like say six months, when a new error is being thrown in Production. Six-month-later-me does not remember what current-me knows now, leading to maintenance hell. Not only do we have a production problem and unhappy users, but I would have forgotten all the little tricks and hacks to get back my dependency hell knowledge.

And most importantly, I have lost the chance and ability to know and understand the application.

## Dependency Limited and Conflict Free

So how to do this? I follow the following rules:

1. I do not use dependencies that have dependencies *that I have to compile*. That means using vendor and open-source *precompiled* libraries that require no additional software installs to use them.
2. I do not use libraries used by dependencies that may conflict. If a vendor library uses another library, I avoid using that other library in any of my code anywhere.
3. Where necessary, I solve my own problems, not rely on third-party, unmaintained code I find on Stack Overflow or Github.
4. I always write my own clean code when performance or maintenance is critical.

I am not saying I do not use dependencies or never look to Stack Overflow or Github for ideas. I'm not that smart. I simply limit my exposure and maximize my ability to read and understand my code and environment, now and in the future, with these limiting rules.

### Looking at Rule 1

For example, lets talk about one of my database library dependencies. Its is written using Boost. Which means that the client library that I need to compile against has a dependency on Boost. Following the first rule, I use their precompiled libraries, not their source code, and since Boost is a dependency, I do not use Boost anywhere else (Rule 2). It's up to the lovely folks at the database company to deal with their dependencies and create good stable libraries and installers for all platforms, and all I do is use their stable binary versions. A nice clean separation of my code from theirs, easy to maintain and easy to deploy.

### Looking at Rule 2

Since we are on Boost, let me stay on Boost. These days, its almost as if you cannot do anything in C++ without Boost. Every answer to every "I'm stuck" question in StackOverflow on C++ seems to be answered by the phrase "Use Boost".

I'm not saying Boost is a bad library, it's not. **It's so awesome that the C++11 standards team nicked all the good stuff from Boost to make the STL for C++11 and C++14.**

But every darn library out there, every example, every potential dependency seems to use different versions of Boost in different ways. And eventually they conflict because some code somewhere uses a deprecated call or side-effect that conflicts with the same call elsewhere.  Following rule 2, I do not use Boost because everyone else seems to. Half of my problems came from other people's code that used Boost badly.

To reiterate, my problem is not with Boost, it's awesome, my problem is with how badly it's used and abused, and rule 2 protects me.

### Looking at Rule 3

We all know there are the piles of code that are just too tedious to write and have been done over and over again. Loggers, data structures, parsers, network interfaces, great ideas, and simple Stack Overflow solutions. It's so tempting to just copy and paste that code, get it to compile and move on. I mean seriously, why rewrite a logger class! [^1] 

Just use one that's out there and move on, no? 

My experience with these have been a case of short term gains with long term pains. Oh sure, I can get it going with less work on my end. But when things go wrong as they always do? Or when the application starts to perform so slowly that nothing seems to fix it? Or its six months later and the pasted code starts to act funny in production?

Rule 3 ensures I avoid these situations.

Keep in mind, example code or Github projects were written with no context or to solve the writers specific problem, scenarios that almost certainly do not apply in my environment or yours. And when things do go wrong, we have no understanding of the code or know how to fix it. **Understanding code is more important that saving a few hours or days of developer time.**

### Looking at Rule 4

Given that I am developing real-time applications for Finance, hence the C++, performance and memory management being critical. The products process vast amounts of data, which means tight control over RAM, CPU caches and even cache-lines are important, and any wasted compute cycles add up in performance degradation. All my vendor dependencies have been tested and put through this wringer, so I can trust them to be as fast and memory safe as possible, or I would have selected a different vendor.

But not much else is, mostly because it was not written or tested to be that way. Under rule 4, the only way I know how to get the fastest application is to write it myself. That way I can see, *and most importantly understand*, where the bottlenecks are, where the memory is going crazy, where threads are running wild and fix it. Copy-pasted code or Github code rarely cuts it.

## My Situation seems Unique. It's Not.

I do understand that my situation seems to be reasonably unique. My applications are large and complex and need to interact with many systems and technologies which means dependency management is critical. The large code base and tiny team environment means that a simple development setup is best. **Maintainable and understandable code is more important than getting it written quickly.** Production issues will cost us a fortune, which means readable, simple and understandable code is critical to being able to detect and correct issues quickly. And the application needs to be fast and correct and reliable.

For most of you, many of these attributes *seem* not to apply. Crazy deadlines mean that dependencies and copy-paste code are *perceived* as the only way to get there. Maintenance is *probably* not your problem. Apps and requirements are straightforward, hardware is ubiquitous and cheap and if it takes a few seconds longer to process, who cares. Good for you if thats your environment.

But mission critical systems need rock solid foundations, architectures and maintainable code. And any additional dependencies, any additional complexities, anything that slows down deployments or maintenance need to be eliminated mercilessly. Sure, it will take longer to write and test. But the cost and time to build dependency limited and conflict free systems pays off handsomely in reliability, maintenance speed and application performance.

No matter your situation, if you cannot clearly understand your development environment and all the application code, you'll never figure it out when the production system gets slow or goes down. Especially after time has passed and you have been working on other projects.

Not so unique after all.

## In Summary

If you are writing anything mission critical, where future maintenance, performance and teamwork is critical, brutally limit dependencies to simplify the development environment, deployment process and maximize your ability to debug and maintain the product. Ensure that all code added to the project needs to be there and is fully understood, and that it does not conflict with any other code in the system.

It means that you will have to write a few more modules yourself, but that investment pays off incredibly later on.

[^1]: A Logger Class: I referred earlier to a logger class as an example of code that has been done hundreds of times over and who the heck is silly enough to write another one. **Me, that's who.** Why? Because I needed a real-time logger that would not in any way slow down the processing on the primary threads of the application. Almost all logging classes are synchronous, you have to pause the thread while the logger spits its results out to screen and file system. That makes sense when you have the time to wait and ensures that log entries are saved before moving on and potentially crashing. Async loggers often collect log entries, then pause everything to batch send (even if they are on alternate threads). But in a real-time system, the huge number of milliseconds (1/1,000 of a sec) needed to append to a file or send a log message kills performance that is measured in microseconds (1/100,000 of a sec). I needed to know just how the logger impacts thread performance, and need to optimize its performance too, and that's why I wrote my own logger.
