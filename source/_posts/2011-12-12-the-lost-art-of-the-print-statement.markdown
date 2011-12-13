---
layout: post
title: "The lost art of the print statement"
date: 2011-12-12 09:28
comments: true
categories: 
---

Debugging software is hard, especially if you were not the original author. All programming languages come with debugging tools, from the arcane GDB to the dead sexy step-through debuggers in Xcode and Visual Studio. But, having watched some newbies recently attempt to debug some code using these tools, I noticed something. With all the data in the world on their screens, breakpoints, stacks, watches and code hovers, the information they needed to solve the bug was being lost is the mix.

When I started programming, the best debugging technique was the print statement.

Not sure what the value of a variable was, print it.

Not sure which branch of an IF gets called, add print statements to each leg.

Not sure the order of a set of calls, add print statements to the top of each function.

Run, read, rinse, repeat.

All modern programming languages have logs and print statements. Javascript has `console.log`, Objective-C has `NSLog()`, Rails has `Rails.logger.info`. Easy to add, easy to use, easy to see the results, easy to comment out when done.

So next time you are stuck in a bug, forget the debugger. Bung in a few print statements and actually see what is going on. I'll bet you find the bug faster because one of the print statements will not make sense.
