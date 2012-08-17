---
layout: post
title: "Expect the Unexpected"
date: 2012-08-08 11:49
comments: true
categories: 
---

There was a panic at one of my client sites today when the reporting software I wrote for them stopped working. Instead of presenting reports as usual, the software threw an unknown error.

WTF, an unknown error!

I wrote the darn system, I know all the errors, because I coded all of them!

A quick glance at the logs indicated that indeed, Passenger was throwing an unknown error when accessing one Rails URL (and all others were working just fine). It’s as if that Rails path just disappeared.

Drilling down the stack of log errors, it turned out to be quite a simple error — a single data point was `nil` instead of the expected number and any calculations or transforms on `nil` throw an error. As they should.

But this number *was* in the input file to the system, as in all previous input files, and verified to be there. And the input file *was* loaded OK, as did all previous input files. So why, on this day, at this time, is there a `nil` when every other day there is a number?

It turns out that the company that sends the file accidentally sent us *two* files today, one being the usual file we expect, and another that we had never seen before *but in the exact same format with the same keys!*. My code processed *both* files, overwriting the correct first file with the garbage from the second file.

The fix was easy, nuke the bad file, reprocess the good file and we’re off and running. Business interruption was insignificant.

But the lesson learned is to **expect the unexpected**. I have now changed the file processing code to check that the file it receives is the one it expects to receive, and ignores all others. That way, when this happens again, as it always does, the software will only process the *good* file.

Next time you see a one-off error, don’t just rectify the situation and walk away, find out what caused the problem, and ensure that it can never happen again.
