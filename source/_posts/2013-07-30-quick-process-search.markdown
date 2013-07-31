---
layout: post
title: "Quick Process Search"
date: 2013-07-30 19:45
comments: true
categories: [ tips-and-tricks, unix ]
---

I am forever starting and running background UNIX tasks, either manually or via `cron` jobs. And I am forever checking to see if they are running or not.

The usual command *I used to use* see if a process was running is 

	ps ax | grep bash
	
Where `bash` is the process that may or may not be running. It gives (headers added):

	  PID TTY         TIME    CMD
	  411 ttys000    0:00.04 -/bin/bash
	  615 ttys001    0:00.04 -/bin/bash
	  773 ttys001    0:00.00 grep bash

There are some issues with this:

1. For long commands with redirections in them, it truncates the command at the width of the terminal (80 columns).
2. I invariably then go looking at other utilities for memory or CPU usage, so there's not enough information.
2. The `grep` itself is found, adding another line to the output.
3. Too much to type all the time, I am lazy.

A better version is:

	ps auxwww | grep bash
	
This gives user, pid, memory and CPU as well as the full command line (headers added): 

	USER             PID  %CPU %MEM      VSZ    RSS   TT  STAT STARTED      TIME COMMAND
	hiltmon          411   0.0  0.0  2433436   1600 s000  Ss    7:44PM   0:00.04 -/bin/bash
	hiltmon          768   0.0  0.0  2432768    596 s001  R+    7:52PM   0:00.00 grep bash
	hiltmon          615   0.0  0.0  2433436   1604 s001  Ss    7:48PM   0:00.04 -/bin/bash

Much better. But even harder to type. And it *still* contains the `grep` line.

So I created a `bash` function in my `.bash_profile` to make it easier:

	# PS with a grep
	function psax() {
    	ps auxwww | grep "$@"  | grep -v grep
	}
	
Now I just type:

	psax bash
	
to get a nice clean result:

	hiltmon          411   0.0  0.0  2433436   1600 s000  Ss    7:44PM   0:00.04 -/bin/bash
	hiltmon          615   0.0  0.0  2433436   1604 s001  Ss    7:48PM   0:00.04 -/bin/bash
	
**Top tip:** A lot of people use this to get the `pid`'s of processes in order to kill them. All distributions now come with the `killall` command, so it is even easier:

	killall stunnel
	
Kills all known instances of `stunnel` that you *can* kill.

The `psax` function has been added to all my logins, and I use it a lot!

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*