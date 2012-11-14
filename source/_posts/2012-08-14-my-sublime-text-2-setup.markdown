---
layout: post
title: "My Sublime Text 2 Setup"
date: 2012-08-14 12:38
comments: true
categories: [Text Editors, Productivity]
---

I have been using Sublime Text 2 for a month or so now, and I still do *not* love it. Here’s hoping TextMate 2 gets it’s game on. But at least I have it working closer to the way I want it to work and look now. Here are the minor changes I have made to make it work for me and how it compares to TextMate 2.

## Packages

Of course, the first thing you do with Sublime Text 2 is install [Package Control](http://wbond.net/sublime_packages/package_control). Why this is not part of the product astounds me, but that’s the way it is. You use Package Control to install the packages you need to run Sublime Text.

Then I installed the following packages (mostly for Ruby on Rails work):

* [Alignment](http://wbond.net/sublime_packages/alignment)
* [CoffeeScript](https://github.com/Xavura/CoffeeScript-Sublime-Plugin)
* [DetectSyntax](https://github.com/phillipkoebbe/DetectSyntax) - so `.rb` files get the right format
* [ERB Insert and Toggle Commands](https://github.com/eddorre/SublimeERB)
* [Git](https://github.com/kemayo/sublime-text-2-git)
* [HTML5](https://github.com/mrmartineau/HTML5)
* [jQuery](https://github.com/mrmartineau/jQuery)
* [rSpec](https://github.com/SublimeText/RSpec)
* [SCSS](https://github.com/kuroir/SCSS.tmbundle)
* [SFTP](http://wbond.net/sublime_packages/sftp)
* [SideBarEnhancements](https://github.com/titoBouzout/SideBarEnhancements/)
* [SublimeCodeIntel](https://github.com/Kronuz/SublimeCodeIntel)
* [Theme - Soda](https://github.com/buymeasoda/soda-theme/) - to make it look useable

I had a few others installed, but they conflicted with each other. Surprised that that happened, had to remove them.

## Defaults

I love the RailsCasts theme, so I copied the `RailsCasts.tmTheme` file to the correct folder (on OS X that is `~/Library/Application Support/Sublime Text 2/Packages/User/`). My **Preferences / Settings - User** looks like:

``` json
{
	"color_scheme": "Packages/User/Railscasts.tmTheme",
	"ensure_newline_at_eof_on_save": false,
	"folder_exclude_patterns":
	[
		".svn",
		".git",
		".hg",
		"CVS",
		".sass-cache"
	],
	"highlight_line": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"rulers":
	[
		80
	],
	"save_on_focus_lost": true,
	"tab_size": 2,
	"theme": "Soda Light.sublime-theme",
	"word_wrap": true
}
```

In short, I set the Soda Light theme as the default dark theme is ugly and use RailsCasts for editor colors, nuke the `vi` support, trigger save on lost focus and fix-up the folder exclude patterns to hide some Octopress folders.

I also changed 2 keybindings, in **Preferences / Key Bindings - User**, I have:

``` json
[
	{ "keys": ["ctrl+shift+d"], "command": "duplicate_line" }, // Like TextMate and BBedit
	{ "keys": ["ctrl+shift+."], "command": "erb", "context":
    [
      { "key": "selector", "operator": "equal", "operand": "text.html.ruby, text.haml, source.yaml, source.css, source.scss, source.js, source.coffee" }
    ]
  }
]
```

And that’s about it.

## Compared to TextMate 2

So now Sublime Text 2 looks just like my TextMate 2 setup:

{% img /images/sublime-textmate-match.jpg 640 230 %}

But there are subtleties that are still driving me nuts:

* TextMate 2 is a Mac application, uses Mac conventions and components, works like a Mac application. Sublime Text 2 does not, whether it’s the look of the find box or the use of the same drop-down for everything from commands to navigation, it’s just not right as a Mac user experience.
* The Bundles a.k.a. Packages in Sublime Text 2 seem half done. I can forgive that the product is new and the bundles need to catch up, but since most of them are just TextMate bundles re-wrapped, I’m surprised they don’t feel like better quality. And there does not seem to be a way to figure out how good a package is until you install it and things go awry.

I’m going to stick with Sublime Text 2 for now, but am keeping an eye out for something better.

See also [Multiple Themes in Sublime Text 2](http://www.hiltmon.com/blog/2012/11/07/multiple-themes-in-sublime-text-2/). And follow me at [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](https://alpha.app.net/hiltmon) on App.Net.
