---
layout: post
title: "The Productive Mac Mindset"
date: 2015-08-15 12:42:13 -0400
comments: true
categories: [ productivity ]
---

I have been using a set of productivity enhancement tools on my Mac for so long now that the standard, out-of-box OS X user experience seems challenging, crawling, cumbersome and somewhat convoluted.

So much so that *it has become frustrating for me to use another person's Mac.*

In this post, I intend to outline how the limited set of productivity tools I use give me "ludicrous speed". *Note that I have invested the time to learn these tools and to create the productivity shortcuts they provide.* Maybe it will help you with ideas to be more productive too.

### Keyboard Maestro

{% img right /images/keyboard-maestro-icon-64.png 128 128 %}

[Keyboard Maestro](http://www.keyboardmaestro.com/main/) is my primary productivity tool. Over the years I have added more and more macros to the point that I forget how to do things without them. It has also replaced other productivity utilities as its functionality has grown. [Keyboard Maestro](http://www.keyboardmaestro.com/main/) initially started out as a way to run a series of commands using keyboard shortcuts and has grown into a tool that can do these from menus, from application launches, startup, disk mounts, even scheduled. If you can imagine it, it can probably do it.

My [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macros include:

{% img right /images/keyboard-maestro-menus.png 173 220 %}

* Launching new Safari windows from a keyboard shortcut, with additional shortcuts for Rails development, the common web applications I open at work or blog posting. For less common sets, I use the menu feature.
* Shortcuts to speed up blog article creation.
* Markdown tools to enable markdown formatting in other applications.
* Setting fixed width text in Mail messages (for code snippets) with a single keystroke.
* Mounting and un-mounting the network shares at work.
* Kicking off [iTerm 2](http://iterm2.com/) sessions, either a single new shell or a set of shells remotely logged into our servers and running key applications. I launch complex development environments with a single keystroke.
* Preventing me from `⌘Q` in Safari and losing all my windows.
* Generating and sending product release notes.
* Creating tweets and [Facebook](http://facebook.com/hiltmoncom/) links for new blog posts.
* Reopening a page in Google Chrome on the rare occasions I need to see Flash content.

{% img right /images/dev-screen.png 320 180 %}

For example, to spin up my test environment which involves launching six applications, log viewers, a web server and a calculation engine, all in different terminal windows arranged so I can see what is going on, I could manually create new terminals for each application, type in the command to launch each one, then rearrange the windows. Which takes a lot of time.

Or press a single key and let [Keyboard Maestro](http://www.keyboardmaestro.com/main/) do it for me.

### TextExpander

{% img right /images/text-expander-icon-64.png 64 64 %}

[TextExpander](https://smilesoftware.com/TextExpander/index.html) then takes over to reduce the number of keystrokes to type almost anything. In many cases, I have [TextExpander](https://smilesoftware.com/TextExpander/index.html) snippets for specific applications.

My [TextExpander](https://smilesoftware.com/TextExpander/index.html) quiver includes:

{% img right /images/textexpander-snippets.png 173 289 %}

* My source code snippets for headers, code blocks and other common patterns. This allows me to use them across IDEs.
* Expansions in the terminal for:
	* Changing to project folders.
	* Launching applications.
	* Managing `git` with fewer keystrokes.
	* Build (`make`) commands.
	* Popular `rake` commands.
* Typing symbols (who ever remembers the keys to press to get these).
* Frequently retyped email content.
* Additional snippets used for blogging in [Octopress](http://octopress.org/).
* Common blocks of Markdown text.

For example, to build my current product, I type `;cdcbs` (which expands to `cd ~/Projects/Maritime/cb/ChesapeakeBayServer`) to change to the product folder, then `;m8i` (which expands to `git pull; make clean; make -j 8; make install`). So much faster.

{% pullquote %}
It has taken a lot of time to create the macros, perfect them and convert them into habits. But the time invested has paid off incredibly. {" These two products on their own as configured enable me to spend more time on the keyboard, more time thinking and programming and significantly less time doing manual labor on the computer. "} And that means I get more done in less time with fewer frustrations and screw-ups.
{% endpullquote %}

### Three More

There are three additional tools that in their own ways complete the limited package: [1Password](https://agilebits.com/onepassword), [Hazel](http://www.noodlesoft.com/hazel.php) and [Mail Act-On](http://www.indev.ca/MailActOn.html).

{% img right /images/1password-icon-64.png 64 64 %}

[1Password](https://agilebits.com/onepassword) does one thing well, it manages all my passwords so I only have to remember one. It speeds me up as I use it as a web site launcher and I never lose time mistyping passwords. `⌘\` in [1Password](https://agilebits.com/onepassword) is your friend!

{% img right /images/hazel-icon-64.png 64 64 %}

[Hazel](http://www.noodlesoft.com/hazel.php) takes care of housekeeping for me, so I do not have to. It cleans up my desktop and downloads folders, it files my bills and creates OmniFocus payment reminders. The hardest part of using [Hazel](http://www.noodlesoft.com/hazel.php) is to figure out what you want it to do for you, setting that up and forgetting about it is the easy part.

{% img right /images/mail-act-on-icon-64.png 64 64 %}

And [Mail Act-On](http://www.indev.ca/MailActOn.html) gives Apple's Mail superpowers. We all get too much email, and, unfortunately, we need to hang on to it. I mainly use [Mail Act-On](http://www.indev.ca/MailActOn.html) for its single key shortcuts to file emails in folders and keep my Inbox clean (but not zero).

### There are Others

{% img right /images/launchbar-icon-64.png 64 64 %}

You may have noticed that the two most popular productivity tools, [LaunchBar](https://www.obdev.at/products/launchbar/index.html) and [Alfred](https://www.alfredapp.com/) are not mentioned. I *used* to use them a lot, and both are still installed, just not running. With all my [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macros running well, I was down to using them as application launchers only. I tried using Spotlight in Yosemite as an Application Launcher, and it worked well enough to stick.

{% pullquote %}
Consider the amount of time you spend performing menial tasks on your computer, launching the same windows, typing in the same commands and text, filing, tidying up, doing the same thing over and over again. Computers are awesome at this, and these productivity tools make it easy to set up and do. {" The money invested in buying these tools and the time invested in setting them up pays off tremendously. "} To the point that the OS X experience without them seems slow and cumbersome.
{% endpullquote %}

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*