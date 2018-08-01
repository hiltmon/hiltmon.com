---
layout: post
title: "The Quick Code Cleanup"
date: 2014-09-02 23:29:19 -0400
comments: true
categories: 
---

The quick code cleanup is a process whereby you run through some or all of the files in a software project and tidy them up. Think about it as the regular tidying of your desk (or room) and filing things away -- versus the rearranging and rewiring of a full code refactor. You can get a lot more done on a tidy desk.

Quick code cleanups can and do include some minor refactoring, but they are mostly about renaming items, reformatting code and commenting on or cleaning up messy sections. No features are added or changed.

So why do quick code cleanups? **Because they save tremendous time as the project progresses.** And the best part is, you do not need to do much thinking or need the zone (See the [Four Hour Rule](https://hiltmon.com/blog/2011/12/03/the-four-hour-rule/)). For example, I just spent the last few hours doing a quick code cleanup while watching the US Open tennis!

Here are some of the things to do in a quick code cleanup:

### Fix Bad Names

Naming classes, functions and variables is hard. Knowing how they *may* be used or evolve is almost impossible beforehand. When you name new classes, functions or variables, you have an idea of how *you think* they will be used. But as the program evolves, these old names may no longer be sufficiently explanatory or correct. 

In a quick code cleanup, you revisit naming after-the-fact, but close enough to remember your thinking, knowing how the elements are *now* being used. You will find that you have a much easier time finding and choosing better names in cleanup. It also means that, when writing new code, you can relax a bit knowing you'll come back and rename the items you are unsure of.

*It makes the code more understandable for later.*

### Fix Lazy Formatting

While coding, we often forget to format our code properly. Or the IDE (I'm glaring at you, Xcode) *helpfully* generates its own code layouts for you.

In a quick code cleanup, you reformat the code to whatever standard you prefer, add white space, and rearrange the functions in files to make more sense. For example, I like to have functions that call each other closer to each other in the file so it's easier to see them on the same screen. At coding time, I may not have written them or know which, at cleanup time I do. I also like to separate *paragraphs* of code with white space and comments, which I add in cleanup. 

*It makes the code a lot more readable and browsable for later.*

### Explain Some Decisions

If you have ever been in a code review you'll know that the most common question is "WTF were you thinking?". We know what we  were thinking when coding, and we remember that thinking for a short while. But we all forget that thinking over time as other thoughts take over.

In a quick code cleanup, you add comments where necessary to explain your thinking. Why did you design a class this way, or write something that way. Or how does this complex calculation work? What was I thinking at the time?

*It makes the code a lot more maintainable for later.*

### Early Cruft Removal

We all create classes and functions, use them for a while, and then replace them. We do *not* always remember to remove unreferenced classes or comment them out from the code base. Later on, when searching for how something went badly wrong, we get confused by this extra code. Is *this* the function called or another? This, to me, is how cruft starts.

In a quick code cleanup, while your mind is fresh, remove all classes and functions that are *not* being used. If you need them again later, you can get them back from source code control. If unsure whether something is being used, use search in your IDE to see if the function or class is referenced (or just comment it out and compile -- if the compile passes, it is cruft).

*It makes code smaller, simpler and less confusing for later.*

### Basic Refactoring

Other than renaming classes and variables, a quick code cleanup also usually entails:

* Pulling up common and duplicated code into functions, or replacing long, complex, deep `if` clauses with function calls
* Adding standard file headers (if necessary)
* Hiding public variables behind setters and getters (one or both) 
* Commenting out or deleting surplus debug statements
* Adding missing `asserts` to document your assumptions

*It reduces the number of potential bugs for later.*

## When to run a quick code cleanup?

I *try* to do this every few weeks on current projects, when the code is still fresh in my mind and when I have some time. This often coincides with a minor release or the few hours at the end of the week when I know I will not have enough time to enter the [zone](https://hiltmon.com/blog/2011/12/03/the-four-hour-rule/) and work on a new feature.

The quick code cleanup may not seem to be a productive use of your time, but it pays off tremendously as the software grows in size and complexity. As the code-base expands, it yet remains understandable, readable, maintainable, simpler and with fewer bugs, enabling you to spend *more* time crafting new code and *less* time figuring out what the hell happened in the past and untangling a knotted mess.

You can start doing quick code cleanups anytime.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*