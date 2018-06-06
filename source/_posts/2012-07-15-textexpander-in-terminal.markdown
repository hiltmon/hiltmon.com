---
layout: post
title: "TextExpander in Terminal"
date: 2012-07-15 10:21
comments: true
categories: [Productivity]
---

I spend a lot of time in Terminal.app mostly running Rails or Git commands. I am also lazy, so I like to use short macros instead of typing in the same thing over and over again. I used to use bash aliases or functions, but I mostly use [TextExpander](http://smilesoftware.com/TextExpander/) snippets now because I like to be sure they don't conflict with internal UNIX commands.

In this post I will show you

* How to setup a TextExpander Group that only runs in the Terminal
* Some of the more common snippets I have added to this group

Lets get started.

## Setup TextExpander Group for Terminal

{% img right /images/textexpander-applications.png 282 274 %}

If TextExpander is only on your menu bar, click the icon, then choose **Open TextExpander**. In TextExpander, create a new Group. I called mine **HL Terminal Commands**. In the **Group Settings** (see below), choose **Only These Applications...** and TextExpander will bring up a list of installed applications (see right). Check **Terminal** only. TextExpander will now only expand these snippets in Terminal.app.

{% img /images/textexpander-group.png 640 357 %}

## Some core Snippets

### Change to Project Folder

One of the first commands I always enter in Terminal is to change to a project folder's code subfolder. It's a lot to type `cd ~/Projects/Kifu/code/kifu` every time, so I created a snippet abbreviated to `;cdki` to do it.

* `;cdki` -> `cd ~/Projects/Kifu/code/kifu`
* `;cdhi` -> `cd ~/Projects/HiltmonDotCom/code/hiltmon.com`

### Git Commands

As we all do, I spend a lot of time typing in Git commands to manage Source Control.  Of course, I use [git-completion.bash](https://github.com/git/git/blob/master/contrib/completion/git-completion.bash) to speed up typing in branch names. Here are some of my snippets for git:

* `;gs` -> `git status`
* `;gm` -> `git merge --no-edit --no-ff ` *(note the space at the end)*
* `;gcd` -> `git checkout develop`
* `;ga` -> `git add .`
* `;gb` -> `git branch`
* `;gcb` -> `git checkout -b ` *(note the space at the end)*
* `;gpo` -> `git push origin`

One thing I like to do is log all commits to [Day One](http://dayoneapp.com) - see [Bread Crumbs in Day One](https://hiltmon.com/blog/2012/01/23/bread-crumbs-in-day-one/). In this case I use a TextExpander cursor position marker to set where I type the commit message, then use it to run a bash macro.

* `;gca` -> `gca "%|"`

The bash macro in `.bash_profile` (OS X) is

``` sh
function gca(){
  msg=$*
  path=$(pwd)
  ~/scripts/LogtoDayOne.rb "@${path##*/} $msg"
  git commit -am "$msg"
}
```

So to commit my current branch and merge it into development I could do the following:

``` sh
$ git status
$ git add .
$ git commit -m "Amazing commit message"
$ ~/scripts/LogtoDayOne.rb "@kifu Amazing commit message"
$ git checkout develop
$ git merge --no-edit --no-ff branchname
$ git push origin
```

or, with TextExpander (showing typing only)

``` sh
$ ;gs
$ ;ga
$ ;gca "Amazing commit message"
$ ;gcd
$ ;gm branchname
$ ;gpo
```

to do the same thing, 62 keystrokes instead of 191! Add that up over a day!

### SSH to Server

SSH to a server takes too much typing, so I use this:

* `;sshxxx` -> `ssh deploy@xxxxxxxx.kifuapp.com`

**Aside**: I like my remote terminals to look different, so I have set the following functions up in my bash profile:

``` sh
function tabc() {
	NAME=$1; if [ -z "$NAME" ]; then NAME="Default"; fi
	osascript -e "tell application \"Terminal\" to set current settings of front window to settings set \"$NAME\""
}

# Change the terminal color when remote
function ssh {
  tabc "Hiltmon-Remote"
  /usr/bin/ssh "$@"
  tabc "Hiltmon"
}
```

Whenever I execute a ssh command, my current terminal gets a new color scheme, which gets restored on exit from the remote session (local to the left, remote to the right).

{% img /images/terminal-compare.png 590 420 %}

### Open with Editor

Launching an editor, then opening a recent folder or file takes too much effort too. Here are my editor launcher snippets:

* `;md` -> `mate .` *(Opens the current folder in TextMate 2)*
* `;sd` -> `subl -n .` *(Opens the current folder in Sublime Text)*
* `'bd` -> `bbedit .` *(Opens the current folder in BBEdit)* 

## Looking for more ideas

If you use TextExpander to speed up your use of Terminal, I'd love to hear about it. Link in the comments or DM me on Twitter [@hiltmon](http://https://twitter.com/hiltmon).
