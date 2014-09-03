---
layout: post
title: "The Quick Code Cleanup"
date: 2014-09-02 23:29:19 -0400
comments: true
categories: 
---

The quick code cleanup is a process whereby you run through some or all of the files in a software project and tidy them up. Think about it as the regular tidying of your desk (or room) and filing things away -- versus the rearranging and rewiring of a full code refactor.

Quick code cleanups can and do include some minor refactoring, but they are mostly about renaming items, reformatting code and commenting on or cleaning up messy sections. No features are added or changed.

So why do quick code cleanups? **Because they save tremendous time as the project progresses.** And the best part is, you do not need to do much thinking or need peace and quiet (See the [Four Hour Rule](http://hiltmon.com/blog/2011/12/03/the-four-hour-rule/)). For example, I just spent the last few hours doing a quick code cleanup while watching the US Open tennis!

Here are some of the things to do in a quick code cleanup:

### Fix Bad Naming

Naming classes, functions and variables is hard. Knowing how they *may* be used or evolve is almost impossible upfront. When you create new classes, functions or variables, you have an idea of what and how *you think* they will be used, but as the program evolves, these names may no longer be sufficiently explanatory or correct. 

In a quick code cleanup, you approach naming after-the-fact, but close enough to remember your thinking, knowing what and how the elements are *now* being used. You will find you have a much easier time finding and choosing better names in cleanup. It also means that when writing new code, you can relax a bit knowing you'll come back and rename the items you are unsure of *soon*.

*It makes the code more understandable for later.*

### Fix Lazy Formatting

While coding, we often forget to format the code properly. Or the IDE (I'm glaring at you, Xcode) *helpfully* generates its own code layouts for you.

In a quick code cleanup, you reformat the code to whatever standard you prefer, add white space, and rearrange the functions in files to make more sense. For example, I like to have functions that call each other closer to each other in the file so it's easier to see them on the same screen. At coding time, I may not have them or know which, at cleanup I do. I also like to separate *paragraphs* of code with white space and comments, which I add in cleanups. 

*It makes the code a lot more readable and browsable for later.*

### Explain Some Decisions

If you have ever been in a code review you'll know that the most common question is "WTF were you thinking?". We all know what we  were thinking when coding, and we remember that thinking for a short while. But we all forget over time as other thoughts take over.

In a quick code cleanup, you add comments where necessary to explain your thinking. Why did you design a class this way, or write something that way. Or how does this complex calculation work?

*It makes the code a lot more maintainable for later.*

### Early Cruft Removal

We all create classes and functions, use them for a while, and then replace them. We do *not* always remember to remove them or comment them out from the code base. Later on, when searching for how something went badly wrong, we get confused by this excess code. Is this the function called or another? This, to me, is how cruft starts.

In a quick code cleanup, while your mind is fresh, remove all classes and functions that are *not* being used. If you need them back again later, you can get them back from source code control history. If unsure whether something is being used, use search in your IDE to see if the function or class is referenced (or just comment it out and compile -- if the compile passes, it is cruft).

*It makes code smaller, simpler and less confusing for later.*

### Basic Refactoring

Other than renaming classes and variables, a quick code cleanup also usually entails:

* Pulling up common and duplicated code into functions
* Adding standard file headers
* Hiding public variables behind setters and getters (one or both) 
* Commenting out or deleting surplus debug statements
* Adding missing `asserts`

*It reduces the number of potential bugs for later.*

## When to run a quick code cleanup?

I *try* to do this every few weeks on current projects, while the code is fresh in my mind and when I have some time. This often coincides with a minor release or the few hours at the end of the week when I know I will not have enough time to enter the [zone](http://hiltmon.com/blog/2011/12/03/the-four-hour-rule/) and work on a new feature.

The quick code cleanup may not seem to be a good use of time, but it pays off tremendously as the software grows. As the code grows, it yet remains understandable, readable, maintainable, simpler and with fewer bugs, enabling you to spend more time crafting new code and less time figuring out what the hell happened in the past and untangling the spaghetti.

You can start doing quick code cleanups anytime.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*