---
layout: post
title: "Build only what you need"
date: 2016-02-28 13:24:14 -0500
comments: true
categories: 
---

<span class="light">A note as a result of a discussion with a colleague.</span>

I had quickly assembled a simple class that triggers periodic function calls from a timer on to a single worker thread. I need this class to ensure that periodic functions get called regularly. Since each call is quick to run (takes under a second), only needs to run every few minutes and can happily be queued behind another quick function, the simple single worker model is perfectly fine for this task.

I then reviewed the code with a colleague.

The colleague immediately declared that someone would abuse this class. They may create additional threads in the called function, he argued, they may trigger long running tasks in the called function, they may create hundreds of competing calls, they may abuse this class for all sorts of non-canonical use cases. He felt the code was therefore too basic, open to abuse and therefore a bad design.

I could build a fully featured, multi-threaded, load limited, time limited, repeating event trigger class architecture. It would take me days to do. And it could easily be coded to prevent the above potential abuse cases. One could successfully argue for this architecture.

But there is no point in developing that if the use-case is *as documented in the class* for short, periodic tasks. Adding worker threads adds complexity that is unnecessary (and the scope of work is OK with a slight delay on calls). Adding limiters increases complexity further and are only needed under abuse circumstances.

**I believe you need to build what you need and no more.**

If the use-case changes, you need to review whether to extend and expand an existing class or create a new architecture for the new case.

**Coding based on *possible*, *potential* or *abuse* use-cases of code is silly and a waste of time.**

Code what you need, design it well, and if a new use-case ever emerges, deal with it then.

<span class="light">Aside: He and I are the only two folks with access to this code, and so only he and I could abuse the class anyways.</span>

“Keep It Simple Stupid”, all day long.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*