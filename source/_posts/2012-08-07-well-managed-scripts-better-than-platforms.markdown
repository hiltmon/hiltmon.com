---
layout: post
title: "Well Managed Scripts better than Platforms"
date: 2012-08-07 12:03
comments: true
categories: 
---

One of the most misunderstood things in computing is the need and power of scripts. Most IT shops seek out platforms, tools and technologies to perform business functions, when a bunch of well architected and documented scripts is all that is really needed.

{% blockquote %}
<strong>script</strong> /noun/

An automated series of instructions carried out in a specific order written in an interpreted computer language
{% endblockquote %}

Over the years, I have seen many organizations go out and buy very expensive platforms and hardware, and hire very expensive staff, without even once looking at the alternative, well managed scripts. As a result, they have had to deal with high costs and slow turnaround times when things change (as they inevitably do). In several of these cases, I would have recommended them to get a good scripting programmer, and let that programmer create a series of well managed scripts, leading to cheaper and quicker implementations and more responsiveness to business change.

## What do I mean by *well managed scripts*?

The common perception of scripting is that some cowboy programmer barfs up some horrible code in an interpreted language, gets it working, schedules it to run and walks away. You are left with obfuscated code that is unmaintainable, but also core to your business, so you just have to hope that it keeps on working.

That is not well managed scripts, that is bad programming.

*Well managed Scripts* follow a series of conventions and standards to ensure that each script is just as readable and maintainable as the next, and that common code is shared between scripts in libraries. Just like a “real” program. In fact, the only difference between a set of well managed scripts and a real program is that the scripts run in an interpreted language and they can all run independently (no main function).

By sharing common code, new scripts can be generated more quickly. By using a naming convention, the right script can be found and run easily. By using coding conventions, each script can be made very readable and maintainable.

What follows are two cases where I believe well-managed scripts are better than a platform, and one case where they are not, all in the financial industry.

## ETL Example

One of the biggest problems facing firms in the financial industry is the volume of data that needs to enter and exit the firm. Unfortunately, there’s no standard format, convention, protocol or structure in use. As a result, each financial firm has to parse a myriad of formats to get data in, and produce another myriad of formats to send data out, as well as try to map the naming of things because everyone is different.

Quite a few of these firms have attempted to resolve this issue by looking for a platform to do this for them. And the big software companies have delivered, calling these systems ETL systems (Extract, Transform and Load). Big software companies like SAS and Microsoft have spent millions developing ETL platforms and licensing them for 5 and 6 figure annual fees. And you know what, these systems are very, very good. They can take data in pretty much any format (extract), provide a plethora of tools and techniques to enable their users to program the conversion of data from one notation to another (transform), and bung that data into any other system or database (load).

But they are horrendously expensive to buy and even more expensive to run. Alongside the license, you need servers and databases, dba’s and system admin staff to keep them running and programmers to code up each ETL run and ensure that it keeps working in a changing environment. And since these platforms are very complex, use their own programming languages and conventions, the staff required is highly specialized, hard to find and very expensive. But users of these platforms do land up with one single platform that does all their ETL as and when they need it.

Or they could write a series of scripts with a few shared custom mapping libraries and be done with it. You see, most scripting languages already have libraries to read and write almost any file type (extract and load), it’s what they do best. The middle component (transform), commonly called mapping, needs to be programmed anyway, whether they script or platform. And in most cases the mapping is the same across many scripts (so they can share the code).  It’s a lot easier and cheaper to hire a scripting programmer that uses a common, well known scripting language that any other programmer can read and maintain. And it’s a lot quicker to change a script when the data changes than to redo it in a platform. The risk is that they can easily lose track of all their scripts unless someone manages them properly and it’s harder to monitor whether the scripts ran successfully or not.

All in all, though, the Total Cost of Ownership (TCO) of a platform to do ETL is way, way more than the TCO with well managed scripts to do the same thing. In this case, ETL is pretty much in the wheelhouse for scripting languages, and in my experience platforms are just overkill. And lets not forget the time, cost and inertia of running a large staff to keep the process going versus having one or two script programmers doing it.

## Risk System Example

Most risk management systems consist of a few very high performance mathematical libraries, a database, a lot of moving, mapping and preparing data as input, and taking the output data and formatting and presenting it. The best language for writing these high performance libraries is C or C++, because it has lots of very good math libraries, is compiled to native code and uses the vector units in modern CPUs (or GPUs if smart) to enable massive amounts of numeric computing in parallel. C/C++ also happens to be the worst language for doing all the other stuff.

It my first hedge fund, the risk system was completely written in C. It had some amazingly great math components and some insanely awful data management code. Fully 80% of the code base was hacks and code to get data ready for the calculations and get the results out. But the biggest issue with the system was that it was very hard to modify and change as the business changed.

In order to make the system more flexible, we extracted the math code and wrapped that code in Perl libraries which did not change that often. We then used Perl to handle the data in, gluing the calculation runs and data out functions, code that changed quite often. The result was that we landed up with a far smaller code base to maintain. We were able to adapt far more quickly to changing data, were able to run the entire system much quicker, were able to detect issues sooner in the pipeline and deal with them, and to then do more risk analysis than before. Adding new math components in C still took time, but the rest was quick, easy and very flexible.

## High Frequency Example

However, there are also times when a platform is not only more desirable, it’s necessary. Take for example a real-time trading algorithm or reporting systems. In this case, the performance of a scripting language is just not good enough. You need platforms that can run and report calculations in real time with real-time data feeds. In the trading algorithm case, you get hundreds of security prices every second. The platform needs to calculate the optimal number of each security to hold, determine if it has enough cash to hold it, decide whether the trade passes compliance rules and decide whether to make a trade or not - in real time. You simply cannot do this in a script, but big expensive platform products like SAS handle this brilliantly.  When faced with the need for high frequency trading in a previous Hedge Fund, we modeled the algorithms in Excel and MATLAB, then ran them in a specialized real-time trading platform to maximize performance and return.

## Script first?

So next time you are looking to automate a business function, instead of looking for a prebuilt platform that requires skilled programmers to run and costs a lot of money, why not try to script it first. If it’s not time sensitive, operates in a changing environment, and is in an area where you want to manage cost, *well managed scripts* may be the best technology solution for you.
