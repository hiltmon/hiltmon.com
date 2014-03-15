---
layout: post
title: "From Tool Maker to Tool User"
date: 2014-03-02 10:04:34 -0500
comments: true
categories: 
---

<span class="light">Abstract: Programming is still seen as a single-language, single-platform tool-maker role. That has not been true for a long time. Over the years, the platforms, tools and libraries available have multiplied. We're tool users now, where a programmer can pick up a new platform with ease, and use the tools available to create complex, reliable products a lot quicker. **That which was impossible then is commonplace now.**</span>

The role of the programmer has changed over the years, from being a certified single language, single platform tool-maker into a [master](http://pragprog.com/the-pragmatic-programmer) of application styles, technologies, use cases and platform tool-users. And when you think about it, the tremendous change in the tools we *can* use and master has steered us here. But we, the industry and the job market still view programmers as singular tool makers (just look at most programming job ads).

Heck, I still see myself as a tool-maker. But that has not been true for a long time. I realize now that I am a tool-user that creates useful products. To use a carpentry analogy, I no longer make the [plane][PLANE], I use a plane and other tools to make tables.

As an exercise, I decided to look at what I do and the tools I use in 2014 against 10 years ago, and the 10 before that, and, since I am old enough, 10 years before that too. **I wanted to find out when we stopped being a tool-makers and became a tool-users.** I wanted to understand how we can do so much today that we could not do then.

Before you read on, think about your own experiences, the tools you made or used and what you use today. When did you change?

## 1984

I was close to ending High School and had a [Sinclair ZX81](http://hiltmon.com/blog/2012/08/01/my-first-computer-sinclair-zx81/). On it, I could create simple [BASIC](http://en.wikipedia.org/wiki/BASIC) programs, mainly utilities and games. There was no [IDE](http://en.wikipedia.org/wiki/Integrated_development_environment), no libraries, no database and the command-line environment was rudimentary. If I needed anything, I had to create it first.

*1 task, 1 platform, 1 language, 0 libraries, 0 IDEs, 0 databases.*

**100% tool maker, 0% tool user.**

## 1994

I was working for a [Systems Integration](http://en.wikipedia.org/wiki/System_integration) company. As a firm, we were engaged to write those large, complex core applications for large complex clients such as utilities and government departments. I, however, worked on one part of one product for weeks at a time.

Our desktops were Intel PC's running new fangled [Windows](http://en.wikipedia.org/wiki/Microsoft_Windows) enabling us to run multiple emulated [VT-100](http://en.wikipedia.org/wiki/VT100) terminal sessions to the hosts we were developing on. The platform was [UNIX](http://en.wikipedia.org/wiki/Unix), the code written in [C][CPGM] (and some [C++](http://en.wikipedia.org/wiki/C++), [lex][LEX] and [yacc](http://en.wikipedia.org/wiki/Yacc)), glued by [shell](http://en.wikipedia.org/wiki/Unix_shell) scripts, the editor was [vi](http://en.wikipedia.org/wiki/Vi), and the database was this new one called [Oracle](http://www.oracle.com/index.html).

Being able to see multiple VT-100 terminal sessions on one screen was leading edge, a huge improvement over the teletypes from before and a huge productivity boost. And using a database meant that data storage and retrieval were written for us. But the tools were rudimentary. We needed to write everything, from the protocols between systems to the libraries that processed the data.

*1 task, 1 platform, 2 languages, 1 library, 1 IDE, 1 database.* 

**90% tool maker, 10% tool user.**

## 2004

I was working at a Finance firm, designing and developing the platform for their business. My time was allocated to a project at a time, with interruptions for support.

It was a [Windows](http://en.wikipedia.org/wiki/Microsoft_Windows) shop. Windows on the desktop, Windows on the server. But code was being written in several languages, [C#][CSHARP] and [HTML](http://en.wikipedia.org/wiki/HTML) for the web applications, C++ for the core mathematics, and [Perl](http://www.perl.org) to glue it all together. My IDE was [Visual Studio](http://en.wikipedia.org/wiki/Microsoft_Visual_Studio) for the C# and C++, [UltraEdit](http://www.ultraedit.com) for Perl. We were using the standard C# and C++ libraries from [Microsoft](http://en.wikipedia.org/wiki/Microsoft), and the magnificent variety of tools available on [CPAN](http://www.cpan.org) for Perl. And the database was [SQL Server](http://en.wikipedia.org/wiki/Microsoft_SQL_Server), back when it still acted like the [Sybase](http://en.wikipedia.org/wiki/Sybase) it was.

On the surface, the changes between 1994 and 2004 seem fundamentally small, but were huge. Fundamentally, still using a C-like language, still writing scripts and still using a database. But [Web Services](http://en.wikipedia.org/wiki/Web_service) libraries built into C# meant that writing server interactions was so much faster and easier. [XML](http://en.wikipedia.org/wiki/XML) serialization made integration easier. Perl could do a whole bunch more and a lot quicker than shell scripts given the CPAN libraries. And the IDE was a dream compared to `vi` with integrated syntax coloring, multiple panes, integrated debugging and a built-in database manager.

But the biggest change was the availability and capability of the libraries at hand. Need to read a CSV, there was a library for that. Need to talk to a server, the protocol was written and included in the platform. As programmers, we had moved to being more tool users than makers because the tools had mostly been written. And I do not think we, or the industry, had realized it yet.

*1 task, 1 platform, 3 languages, 3 libraries, 2 IDEs, 1 database.*

**20% tool maker, 80% tool user.**

## 2014

I work at another Finance firm during the day and my own business in my spare time. I am developing yet another internal platform as well as web applications and native mobile applications for clients. The net variety of work is brilliant.

Our client platforms include Windows, [OS X](http://en.wikipedia.org/wiki/OS_X), [Linux](http://en.wikipedia.org/wiki/Linux), [iOS](http://en.wikipedia.org/wiki/IOS) and [Android][ANDROID]. Our servers are mostly Linux with a few Windows Servers as needed. Code is being written in [Ruby](https://www.ruby-lang.org/en/), C++, [JavaScript](http://en.wikipedia.org/wiki/JavaScript), [Python](http://www.python.org), [R](http://www.r-project.org) and of course [Objective-C](http://en.wikipedia.org/wiki/Objective-C). The IDE's in use include [Xcode](http://en.wikipedia.org/wiki/Xcode), Visual Studio, [vim][VIM], [Sublime Text](http://www.sublimetext.com) and the lovely [TextMate 2](http://macromates.com). And when it comes to libraries, we use a lot, including [Rails](http://rubyonrails.org), [Sinatra](http://www.sinatrarb.com), [JSON](http://json.org), [NumPy](http://www.numpy.org), [Pandas](http://pandas.pydata.org), [STL](http://en.wikipedia.org/wiki/Standard_Template_Library), Apple's [Foundation Kit](http://en.wikipedia.org/wiki/Foundation_Kit) and more. And our databases run on SQL Server, [PostgreSQL](http://www.postgresql.org), [MongoDB](http://www.mongodb.org) and [Redis](http://redis.io).

Again, the fundamentals look the same since 2004. Still working the web services angle, C-like languages and scripting tools. But so much more productive. There is a library and a platform and a tool for everything now, no need to write your own. The time taken from idea to delivery has been halved and halved again. It's all about choosing the right tools and using them effectively.

*3 tasks, 5 platforms, 6+ languages, 10+ libraries, 4 IDEs, 4 databases.*

**0% tool maker, 100% tool user.**

## From Maker to User

When I started working we had to be proficient in one platform, one language and one database. It took weeks and months to go from requirements to design to delivery because we had to write everything ourselves and our tools were simple. Support and maintenance were hard. *We were tool-makers.*

In contrast, these days we regularly switch between languages, platforms, and tools to create web, native and hybrid products. The time taken from idea to delivery is days or weeks because it often involves finding the right library, learning how to use it and coding the use case we need. The platforms that we deploy contain so much functionality that most of the work is done for us. And we can do so much more in the same amount of time. *We have become tool-users.*

Back then, the tool-maker had to be able to program at a low level and know all the nuances of the platform. Now the tool-user needs know what tools and libraries are out there, to learn them and to use them, oftentimes platform agnostically. Aside: But we still hire as if we are looking for tool-makers, singular platform/language programmers.

We still need the tool-makers, the ones who create the platforms, languages, libraries and IDE's. But the majority of us have lost that skill if we ever had it. The point is that *using* these tools, the products we tool-users create are better, faster, more reliable, easier to extend than ever before and we produce them so much quicker.

And because we *use* these tools, we can do a lot more every day and create a lot more products. Just look at the scope of work and the numbers above. Back then we worked on a single component of a single product for weeks at a time. Now, we work on a portfolio of products simultaneously. 

Back then, as tool-makers the work we do now was not possible. Now as tool-users, it is what we do all the time.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[PLANE]:	http://en.wikipedia.org/wiki/Plane_(tool)
[CPGM]:	http://en.wikipedia.org/wiki/C_(programming_language)
[LEX]:	http://en.wikipedia.org/wiki/Lex_(software)
[CSHARP]: http://en.wikipedia.org/wiki/C_Sharp_(programming_language)
[ANDROID]:	http://en.wikipedia.org/wiki/Android_(operating_system)
[VIM]:	http://en.wikipedia.org/wiki/Vim_(text_editor)