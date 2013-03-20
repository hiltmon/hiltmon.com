---
layout: post
title: "Sharing Bash Profiles across Computers"
date: 2013-03-12 13:48
comments: true
categories: 
---

If you use more than one computer, keeping your *dotfiles* in sync is difficult. You either need to run a sync program like [ChronoSync](http://www.econtechnologies.com/pages/cs/chrono_overview.html) or set up your own `rsync` scripts. **And then remember to run them.**

I'm lazy, I just want it to work. So here is a lightweight way to share your key *dotfiles* across computers using [Dropbox](https://www.dropbox.com).

Create a folder in Dropbox called `Scripts` and save your *dotfiles* there:

	$ cp ~/.inputrc ~/Dropbox/Scripts/inputrc.txt
	$ cp ~/.bash_profile ~/Dropbox/Scripts/bash_profile.sh
	
*Note: The leading dots have been removed in Dropbox so the files are not hidden and will sync. I also add file extensions to make editing them easier.*

Now that they are shared on each computer, replace your `~/.bash_profile` with:

``` bash
# Copy my shared inputrc (may require 2 loads)
cp ~/Dropbox/Scripts/inputrc.txt ~/.inputrc

# Use my shared profile
source ~/Dropbox/Scripts/bash_profile.sh
```

I have this saved as `use_this_bash_profile.sh` and, on each computer, just once

	$ cp ~/Dropbox/Scripts/use_this_bash_profile.sh ~/.bash_profile

Boom, edit *dotfiles* once, shared on all computers automatically.

*Bonus Tip: Plonk all your other common scripts in the same shared folder and add it to your PATH.*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
