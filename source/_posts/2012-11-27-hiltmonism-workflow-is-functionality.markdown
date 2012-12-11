---
layout: post
title: "Hiltmonism - Workflow is Functionality"
date: 2012-11-27 17:39
comments: true
categories: Hiltmonism
---

Functionality, *the range of operations that can be run in a computer system*, is the foundation upon which all software product collateral, designs, discussions and comparisons are based. Customers buy on functionality. Developers create functionality. Users question *what* the product can do.

That is fine, but it’s not the whole story.

The right question is not *what* operations exist (or should exist), it’s *how* these operations work together, how the functionality flows. How can you tell which operations have been performed, and what operations need to be performed next? That is workflow. The product’s collateral should tell the customer *how* the workflows in this software helps them run their business better. The workflows in a software plan should tell the developers what functions are needed and which can be ignored. The workflows in software help users learn and track what they are doing.

I believe that great software is based on great workflow. I my opinion, the best software has only the necessary functionality needed to support its workflows. Which means that the developer has focussed on how *best* to get things done and on only the operations necessary to do it. Quality, not quantity. There is not 5 ways to do something, there’s the one *best* way. Easy to learn, easy to use, easy to fix, easy to understand.

{% pullquote %}
On the other hand, software that offers an insane amount of operations and no workflow is very hard to use. Either the user has to figure out which operations to use when, or they need trainers and consultants and manuals and lots and lots of implementation money to get it going. {" Sure, high functionality software is more powerful, but only the powerful can use it. "} Interestingly enough, I see a lot of software that started with a few flows, but then got patched so many times to suit different users’ needs that the operation count went crazy and these new operations were not integrated into existing flows.
{% endpullquote %}

You can always tell if software was designed for functionality instead of flow:

* Each screen displays an incredible amount of detail. Instead of providing the *information* the user needs, they get to see the raw data and have to interpret it themselves. Workflow based systems show only the pertinent information on screens.
* There is a dizzying number of items on each application menu or toolbar. I’ve seen systems where you need a 21” screen just to fit the menus on-screen. How the heck is a user supposed to work through all of these and know which apply, which to use next and what each one does. Workflow based systems only show the applicable actions.

When using applications, the user really needs to know the following:

* How do I start a process or workflow to do something
* Where am I now in the current workflow
* What should happen next
* When is the process complete

You’ve all seen hack solutions to this. Microsoft’s Wizards are a great example of using flow to hook together functionality to help users achieve a complex goal, but the wizards themselves are a hack because users can perform each step manually using the menus. Think Windows multistep next, next, next wizards to install software vs OS X drag and drop vs Linux `yum`.

On the other hand, [Adobe’s Lightroom](http://www.adobe.com/products/photoshop-lightroom.html) has a fantastic flow to help photographers process their work. First you manage the upload and storage of the photos (Library), then you process them (Develop), then you release them (Book, Slideshow, Print or Web). There is an incredible amount of functionality in this product, but the user only gets to see and use what’s necessary at each step.

Now think about how you work on your own. How do you use software to perform your own workflows.

In my case, for example, I have a blog writing flow. I start with the idea in [nvAlt](http://brettterpstra.com/project/nvalt/), structure the thoughts in [MindNode Pro](http://mindnode.com), write a draft in [Byword](http://bywordapp.com), come back later and revise a few times, then finally post it to the site. The functionality I need is available at each step, and at a glance I can see where an article is up to.

The above is a simple workflow using simple systems. I could replace some of the simple tools I use with more complex ones (e.g. MS Word instead of Byword) and stay in the flow, but it would be harder to execute and even harder to explain it to others. The thing is, complex systems that have massive functionality can be designed (or customized) to implement flow too, just as easily. All you have to do to focus on workflow is to:

* Have a workflow status for all things. This may be a simple as a file name, or a folder location, or as complex as a state machine status in a database field.
* Always have an indication on screen what to do next (if it’s a complex integrated system). If a user opens a trade on a financial system, the status should indicate whether it has settled and what next the user needs to do.
* Only show actions that apply to this element in this state. Get rid of all the menus and buttons that are unrelated. Users can then see the things they can do with the current element and not be confused by all the other unrelated operations in the system.
* Either pick a product that implements a single best flow, or, if unavailable, pick a flow and try it out. Use it for a time and get a feel for how well it works (where am I, what can I do now, what shall I do next). If the current flow does not work, pick another, and try that out. Eventually you’ll fins a workflow that will make sense.
* Eliminate useless steps in the workflow. One of my big bugbears is watching people execute operations in systems that are unnecessary, but since the operation exists, they feel they have to do so. Fewer operations in a workflow implies higher productivity.

Whether you am designing a small reporting application or an end-to-end Hedge Fund management system, always focus on the flow. That helps you to choose *how* things should be done and prioritize which functions to implement. It makes your software so much easier to use as the visible functions are workflows which are simple, clear, and display only the actions users can and need to take.

Workflow is functionality, the best operations sequenced together in the best way possible. And that makes better software.
