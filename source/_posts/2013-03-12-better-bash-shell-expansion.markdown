---
layout: post
title: "Better Bash Shell Expansion"
date: 2013-03-12 12:33
comments: true
categories: [ Tips and Tricks ]
---

I've been doing a lot of work on TextMate 2 plugins recently and the way shell expansion works in the terminal has been annoying me. Here are some tips to 

* speed up access to the `Application Support` folder, 
* create case insensitive tab completions, 
* reduce typing to `cd` to common folders 
* and to reuse the TAB key for additional completions.

### Getting to Application Support

The TextMate bundles I am working on are hidden in the **Library** → **Application Support** Folder. If you type this in your shell (⇥ is the TAB key):

	$ cd ~/Library/App⇥
	
I'll bet it completes to `cd ~/Library/Application\ S` and stops. That's because there are two folders that could match: `Application Scripts`  and `Application Support`. Since I never need to use `Application Scripts`, I'd like bash completion to ignore it.

Add the following in your `.bash_profile` file:

``` bash
# So I can tab to Application Support
FIGNORE=".o:~:Application Scripts"
```
	
The `FIGNORE` shell variable tells bash completion to ignore files or folders with the matching patterns (colon separated list). Quit and restart your terminal and 

	$ cd ~/Library/App⇥
	
correctly maps to

	$ cd ~/Library/Application\ Support/
	
Thanks Allan Odgaard for the tip in [Path Completion (bash)](http://sigpipe.macromates.com/2012/08/10/path-completion-bash/).
	
### Case Insensitive Completion

I drive myself nuts with case sensitive file and folder names, and then using the wrong case when attempting completion in a shell. I often type 

	$ cd ~/l⇥
	
instead of 

	$ cd ~/L⇥
	
To get to `~/Library`.

To get case-insensitive completion, add the following to a file called `~/.inputrc` (`.inputrc` in your home folder):

	set completion-ignore-case on
	
And restart your terminal. Tab completion will now work no matter what case the file or folder name is.

**Tip**: If you want it to work with hyphens and underscores as well, add:

	set completion-map-case on

### Shorter CD

All my code and projects are in `~/Projects/`, so I often need to type

	$ cd ~/Projects/Kifu/code
	
to get to the code base on [Kifu](http://www.kifuapp.com). I also have a `Pictures` and a `Public` folder so tab completing `cd ~/P` is a pain (see below).

Then I learned about the `CDPATH` variable in bash. Add folders to this and the `cd` command will look there as well for the folder you want. In your `.bash_profile`:

	# So I can cd to projects quickly
	CDPATH=$CDPATH:$HOME/Projects
	
Now I can type

	$ cd Kifu/code
	
from anywhere to get to the same place. 

**Warning:** Using `CDPATH` can screw up some scripts where the `cd` will work on your machine and not on others, use with care.

Also, in OS X, tab completion does not work with `CDPATH`, you need to type in the full folder name, with the correct case. Or you could install `bash-completion` using HomeBrew or MacPorts, something I choose not to do ([Instructions here](https://github.com/bobthecow/git-flow-completion/wiki/Install-Bash-git-completion)).

*Aside: For more frequently accessed folders, I use [TextExpander](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Ftextexpander-for-mac%252Fid405274824%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30) snippets to reduce typing; in this case, the expansion of `;cdki` takes me to the same place. I just don't create expansions for all projects. Yes, I know, I could just as easily use shell `alias` to do the same.*

### TAB for more completions

In my `.inputrc	, I also have

	set mark-symlinked-directories on
	set show-all-if-ambiguous on
	
The first line just makes symlinks look better, the second is brilliant. If there are ambiguous files that *could* match your tab completion, `show-all-if-ambiguous` shows them all and returns you the same prompt to help you type more to get a match.

So typing

	$ cd ~/P⇥
	
Presents the expansion options:

	$ cd ~/P⇥
	Pictures/ Projects/ Public/
	$ cd ~/P

Thats *nice* but I'd like to tab through the options instead. Add this to your `.inputrc` and restart the terminal:

	TAB: menu-complete
	
So typing

	$ cd ~/P⇥
	
now gives

	$ cd ~/Pictures/
	
Press TAB again gives

	$ cd ~/Projects/
	
*Update*: Thanks to Brett Terpstra's [Quick Tip: some .inputrc fun](http://brettterpstra.com/2011/09/25/quick-tip-some-inputrc-fun/), you can use SHIFT-TAB to complete in reverse, just add this to your `.inputrc`:

	"\e[Z": "\e-1\C-i"
	
### Summary

My .inputrc

	set completion-ignore-case on
	set mark-symlinked-directories on
	set show-all-if-ambiguous on
	TAB: menu-complete
	"\e[Z": "\e-1\C-i"

Parts of my `.bash_profile`

	# So I can tab to Application Support
	FIGNORE=".o:~:Application Scripts"

	# So I can cd to projects quickly
	CDPATH=$CDPATH:$HOME/Projects
	
*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
