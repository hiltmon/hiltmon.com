---
layout: post
title: "Fast SSH Windows with iTerm 2"
date: 2013-07-18 22:14
comments: true
categories: [ Macintosh ]
---

I have a bunch of Linux boxes that I need to access via SSH, whether to install things, start or stop processes or browse log files.

But it is a pain to have to launch a new terminal window and type in the whole SSH command line:

	$ ssh hiltmon@servername.domainname.local

Yep, I am that lazy. Or really, I do this so often I needed a faster way to do this.

Enter [iTerm 2](http://www.iterm2.com/#/section/home) profiles with shortcut keys. You can SSH to any of your servers by pressing a single keystroke, cool huh? For example, to access my *Farragut* server in a new [iTerm 2](http://www.iterm2.com/#/section/home) tab, I press `⌃⌘F`, to access *Hipper*, `⌃⌘H`. Here's how to set it up.

## Using iTerm 2 Profiles

In [iTerm 2](http://www.iterm2.com/#/section/home) preferences, access profiles and add a new profile. I name these after the my server *colloquial* names (because who can remember those IT names like `XYZZYDEVDBWX907.domainname.local`). 

{% img /images/iterm-profiles.jpg 700 410 %}

Set the shortcut key you want to use, and input the full SSH command:

	ssh -R 52698:localhost:52698 hiltmon@servername.domainname.local

The -R port mapping enables me to use `rmate` from these terminals.

And that's it.

To activate a new terminal tab and SSH into that server, just press the shortcut key.

### Bonus Top Tips

I change the `PS1` on each server to show the colloquial name, so at a glance you can see which server the terminal window represents. Add the following to `.bash_profile` or whichever file configures your shell (In this case, the colloquial name is *Farragut*):

```
...
# \u -> user, \W is basename, the rest are terminal colors
PS1='\[\e[0;35m\]\u\[\e[0;33m\]@\[\e[1;34m\]Farragut:\[\e[0;33m\]\W \[\e[0m\]\$ '
...
```

{% img right /images/iterm-ps1.jpg 181 58 %}

Which gives us this:

I also slightly change the terminal background color and the colors used in the prompt, not enough to make it garish, but enough to tint the black and change the look. That way my eye can sense different terminals by the slight color variances as well.

## Other Options

You could use [TextExpander](http://smilesoftware.com/TextExpander/index.html) macros, but that requires you to create a new terminal first, more keystrokes. I used to do this until I found these profiles.

If you have [Keyboard Maestro](http://www.keyboardmaestro.com/main/), you could create AppleScripts to create new terminal windows and launch SSH sessions.

If you have [Alfred 2](http://www.alfredapp.com) you could use scripts in workflows to launch a new SSH terminal.

Or you could even use the free [Shuttle](http://fitztrev.github.io/shuttle/) app that puts your list of SSH sites in your menu bar.

Or just use [iTerm 2's](http://www.iterm2.com/#/section/home) profiles.

*Is it not wonderful that we can each find our own way out of an unlimited number of ways to do the same thing, and all be cool about it.*

Related Reading: [Make iTerm 2 more Mac-like](https://hiltmon.com/blog/2013/02/13/make-iterm-2-more-mac-like/)

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*