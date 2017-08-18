---
layout: post
title: "2011 Platforms - Objective-C and iOS"
date: 2011-12-26 11:54
comments: true
categories: 
---

*Part 1 of the platforms I used in 2011 to make products. See [Part 2 - Ruby on Rails](https://hiltmon.com/blog/2011/12/26/2011-platforms-ruby-on-rails/).*

I spent the first half of 2011 writing iOS applications in Objective-C. It's not my first experience with Objective-C, I wrote a Mac app in 2008, and two iOS apps in 2010, so these notes are really about my entire experience with the technology.

<!--more-->

I do remember when I first started using Objective-C and thinking that it was the ugliest programming language of all time. All those square brackets and colons, the odd formatting and needing to write code like Yoda speaks `[there isNoTry:justDo];`. I also did not like the verbosity, I am still a horrible typist and the more I have to type when coding, the more mistakes I make.

But the libraries provided by Apple for Mac and iOS were great, easy to read, understand, learn and use. I always believe that great libraries make a language, which explains my dalliance with C# for such a long time. Microsoft got it right in .Net 1.0 and 2.0 with the libraries (and ruined it in 3.0 and later). It also explains why I think Java is terrible, the language may be sane, but the plethora of conflicting libraries meant that you cannot create a Java application and use all the libraries you want because their dependencies conflict.

Objective-C really clicked when I realized that it was really Smalltalk with a C-like syntax. Smalltalk was the original Object Oriented language and it had one amazing feature, dynamic binding. Dynamic binding means that objects in Smalltalk are bound (can talk to each other) at *runtime* instead of at compile time like in C#, Java and C++.  Which means you can change things on the fly, you can create a far more elegant and decoupled architecture and not fight your compiler the whole way.

Of course, dynamic binding has its faults. You need a fast message passing architecture to make it work. C++ solved this with vtables, a table of pointers to the functions in the class, that are statically linked at the end of a compile. Objective-C uses a really fast `objc_msgSend()` call to find and bind at runtime without the static links. Debugging becomes a problem, because you cannot predict at compile time whether the actual receiver object is one that can handle the message.

The win comes in the architecture, a sane object model, and great use of patterns, especially the delegate pattern.

Xcode on the other hand started off as my enemy. I had migrated from Visual Studio on Windows as my primary IDE, and I was very comfortable with its idioms.  Xcode was different. Visual Studio had projects and dependencies, Xcode had targets. Visual Studio has a nice tabbed interface, Xcode had lots of windows everywhere, or even worse, no tabs in single window mode. Visual Studio's autocomplete was brilliant, Xcode, not so much. Visual Studio's debugger was amazing, `gdb` felt old.  Switching to Xcode was hard.

But I finally got it, mostly through perseverance, and through realizing that the target approach did in fact actually work. And then they changed everything on me and released Xcode 4. Xcode 4 hit the spot for me as a Mac based IDE. The UI made sense to me, the keyboard idioms made sense, the jump bar worked. I developed my first two iOS products in the buggy beta's of Xcode 4 and compiled the final releases in Xcode 3. And Instruments made memory checking, performance testing and other tasks so much easier.

These days I look fondly on Xcode and Objective-C. I am looking forward to my next Mac or iOS project. Looking forward to using Xcode and using the new LLDB, ARC and Instruments packages. Looking forward to making my next great native app.
