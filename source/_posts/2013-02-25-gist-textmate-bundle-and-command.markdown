---
layout: post
title: "Gist TextMate Bundle and Command Line"
date: 2013-02-25 15:44
comments: true
categories: [ TextMate, Productivity ]
---

I was having a conversation on Twitter with Shawn Hansen ([@geekles](https://twitter.com/geekles)) this weekend and he mentioned that [Sublime Text 2](http://www.sublimetext.com) has a great plugin for Github Gists, and [TextMate 2](https://github.com/textmate/textmate) was missing this awesomeness. 

Not anymore (the Oscars were on).

{% img left /images/textmate-gists-menu.png 158 132 %}

Announcing the first release of my [TextMate 2 bundle](https://github.com/hiltmon/Gist.tmbundle) and a [separate command line tool](https://github.com/hiltmon/gist) for retrieving, creating and updating GitHub Gists.

The main difference between this and other implementations is that this one *caches* gist mappings (gist id to file names in `~/.gists`) so you don't have to remember them (and because TextMate 2 has no way to save user attributes on opened files). This implementation also leaves the gist URL on the clipboard for OS X users (which makes it quicker to blog with gists).

With these tools you can:

{% img right /images/textmate-pick-gists.png 285 329 %}

* Download and edit any public gists from within TextMate 2 or the command line (and since they both use the same code-base, they can be interchanged).
* List up to 100 (API limit) of your own gists and pick which to download and edit.
* Update gists with a keystroke in TextMate or from the command line *without knowing the file's gist ID*.
* Easily create new public and private gists of files you have and paste their URLs where needed.
* View the gist and its comments on the web

This *first* version of the tools *does* support downloading multi-file gists, but updates and creates apply only to single files *at this stage*.

Follow the instructions on each to install them, and don't forget to set up the authentication as described in their README files before use.

> Get the [TextMate Gist.tmbundle](https://github.com/hiltmon/Gist.tmbundle) on GitHub.

> Get the [Command line Gist](https://github.com/hiltmon/gist) on GitHub.

I would love to hear how you use these, what additional features you'd like to see in them, and feel free to fork and contribute to them as well.

**This is at best beta level software and has been tested and run on one and only one machine (mine) with the current alpha version of TextMate 2! You takes your chances by installing and using it.**

Enjoy.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*

