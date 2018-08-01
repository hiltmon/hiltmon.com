---
layout: post
title: "Keep long running UNIX commands alive"
date: 2014-04-19 12:43:53 -0400
comments: true
categories: 
---

Here's the situation: you have a UNIX script that takes a long time to run, but gets killed when your computer goes to sleep and the SSH terminal or VPN disconnects. *Ouch*.

I know of three ways to kick long running scripts off and not worry about sleeping computers or disconnections: `nohup`, `disown` or `tmux`.

## Simple: `nohup`

From the `man` page:

	nohup -- invoke a utility immune to hangups

Which really does not tell the story. When the parent terminal session terminates, it sends a hangup (SIGHUP) to all child processes, causing them to terminate as well. `nohup` tells a process to ignore that hangup.

However, if the process is still part of the primary thread of a terminal, it dies anyway because it's parent terminates.

To kick off a long running process on unix, type

	$ nohup <the command> &
	
This tells `<the command>` to ignore hangups, and detaches the process from the current terminal, so the kill signal is also ignored.

To see what is going on in this thread:

	$ tail -f nohup.out
	
`nohup` helpfully appends standard output and standard error to this file.

Go ahead and try it, kick off a command using `nohup ... &`, close the terminal, create a new terminal session and tail the **nohup.out** file to see that the process is still running.

## Oops I Forgot: `disown`

If you forget to kick off a process using `nohup`, never fear, `disown` is your friend. The only negative is that this does not create an output file, so you need to use `ps` to track progress.

To `disown` a process, you need to suspend it (⌃Z), put it into the background (like the `&` in the `nohup` line) and then `disown` it as follows:

	# press Ctrl+Z to suspend the program
	$ bg
	$ disown

It's now safe to let the terminal session die, the process will run to completion.

## Complex: `tmux`

If you already use `tmux` sessions, this is the simplest solution. If you do not, you need to set it up before you run the long running command.

To start a `tmux` terminal, just type

	$ tmux new -s long-running-session
	
Run the program in this session as normal, no need for `nohup` or `disown`.

Before closing the terminal, detach the session:

	$ tmux detach
	
Or `⌃b d` from within the `tmux` terminal.

To get it back later, just re-attach the session:

	$ tmux a
	
or

	$ tmux a -t long-running-session
	
And the long running command will still be running (or completed).

I won't go into setting up `tmux`, Daniel Miessler wrote a great [tmux Tutorial and Primer](http://www.danielmiessler.com/study/tmux/) to show you how to do this.

## iTerm 2

Since I use iTerm 2 profiles to `ssh` to my servers (See [Fast SSH Windows with iTerm 2](https://hiltmon.com/blog/2013/07/18/fast-ssh-windows-with-iterm-2/)), the simple `nohup ... &` version is the one I use all the time to kick off and log long-running UNIX commands.

For example, to run a long running command on **Farragut**, I

- Launch iTerm 2: `⇧⌃t`
- `ssh` to Farragut: `⌃⌘F`
- `nohup <the command> &`

And if my VPN session disconnects, I can always get back an see what happened in the **nohup.out** file.

Enjoy.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
