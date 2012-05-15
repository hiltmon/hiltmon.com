---
layout: post
title: "Application Context Packs"
date: 2012-04-26 09:49
comments: true
categories: 
---

When developing in Rails, I use a certain pack of applications; when coding for iOS, I use a different pack of applications; and when in a blogging context, I use a third pack of applications. And then there is the regular set of applications that I usually leave running. Starting and switching between these contexts used to take time, until I found a better way.

**The Old Way**

After a clean reboot, I would then have to go through the same dance every time, launch the regular applications manually. Start Mail.app, [OmniFocus](http://www.omnigroup.com/products/omnifocus/), [Billings](http://www.marketcircle.com/billings/), [nvAlt](http://brettterpstra.com/project/nvalt/), [Twitterrific](http://iconfactory.com/software/twitterrific), [Reeder](http://reederapp.com/), iChat and [Skype](http://www.skype.com/), waiting for each to launch before clicking the next one.

Then I would choose what to do next and start the application pack for that context. If I were to be programming in [Rails](http://rubyonrails.org/), that means two terminal sessions, [TextMate](http://macromates.com/), [BBEdit](http://www.barebones.com/products/bbedit/index.html) and Safari. If iOS, then it's Xcode, [BBEdit](http://www.barebones.com/products/bbedit/index.html) and [Photoshop](http://www.photoshop.com/), blogging, [MarsEdit](http://www.red-sweater.com/marsedit/) and Safari.

To switch contexts, I would manually close the unnecessary applications, and then manually launch the new ones. And then configure them for the project I was working on.

This was painful, slow, and I often forgot to either close unnecessary applications or launch the ones I needed.

**The New Way**

I have set up a bunch of [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macros and shortcuts to take care of all of this, and use [TextExpander](http://smilesoftware.com/TextExpander/) snippets for configuration where necessary. Here's how it works.

I have setup a Keyboard Maestro macro mapped to `⌃⌥⇧⌘W` that opens all my standard applications (called 'Start All'). This macro launches all my regular applications, then hides the Skype window. One keystroke, and everything is on. I boot, I hit this combination and it's all done. I also have a matching `⌃⌥⇧⌘Q` ('self-destruct') macro that kills everything, one keystroke and all my running apps terminate.

To switch contexts, I have a series of context macros linked to the *same* key combination `⌃⌥⇧⌘C`. In Keyboard Maestro, if you use the same key for more than one macro, it displays a panel for you to choose from.  Here's mine:

{% img /images/application-context-panel.png 223 169 %}

I can either use the mouse to select a context, or just press `1` for the first, `2` for the second, etc. The macros themselves are pretty simple: if I am already in that context, it terminates the context applications, else it launches them. It determines whether I am in a context by checking if the key application for that context is running. For example, if Xcode is running, then triggering the Xcode context terminates it, else it launches it.

This works great in my blogging context. Trigger the macro and a terminal session is opened *in my blog folder*, ready for me to create a new post. I have modified the `new_post` code in [Octopress](http://octopress.org/) to launch [Byword](http://bywordapp.com/). When I am finished blogging, I trigger the same macro and Byword and Terminal are closed. Back to a clean system.

It's *almost* same for programming in Rails. Trigger the Rails context and Terminal, TextMate, BBEdit and Safari all launch. The problem is that I work on multiple rails projects at the same time. I could have simply created a context for each Rails project, but given that I bounce between Rails projects while staying in the same context, having to quit and launch the same application pack just wastes time. Instead, I have created a set of TextExpander snippets to handle the configuration of the context.

For example, when I wish to work on [Kifu](http://www.kifuapp.com/), I do the following:

* Launch the Rails Context using `⌃⌥⇧⌘C` and then press `2`. This launches my Rails application pack and leaves me in the terminal.
* I type `;cdki` which TextExpander expands to the Kifu source folder path and press enter.
* Type `;md` (which expands to `mate .`) to open the project in TextMate which is already loaded.

And I'm ready to program. Everything I need is loaded, configured and ready for action.

And when I am finished, `⌃⌥⇧⌘C` and `2` again terminates them all. Back to pristine.

**Dealing with OS X Lion**

I am very comfortable with this workflow, but a few OS X Lion features get in the way. The first is the application resume feature. Since I may be using the same application in different contexts, I sometimes do not want the state from the previous context to be resumed in the new context (and sometimes I do). I have therefore gotten into the habit of hitting `⌘W` a few times on the main context application to close all windows before triggering the context switch.

The second is that Lion resumes all applications on a reboot. Most of the time this is OK, but I want control. So I usually hit self-destruct `⌃⌥⇧⌘Q` before rebooting so I don't have to uncheck that darn checkbox to prevent it.
