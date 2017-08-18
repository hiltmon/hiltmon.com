---
layout: post
title: "My TextMate 2 Setup"
date: 2013-04-15 14:42
comments: true
categories: [Text Editors, Productivity]
---

I switched back to [TextMate 2][github] from [Sublime Text 2][sublimetext] full time a while back and I am really happy with the way I have it looking and working. My "[My Sublime Text 2 Setup][1]" post is quite popular, so I though I'd create the same for TextMate 2.

{% img /images/textmate-themes.jpg 600 240 %}

<!--more-->

## Theme

I am using my [CombinedCasts][2] theme which merges a modified RailsCasts theme for coding and a light theme for markdown and text editing. You can download the [CombinedCasts.tmTheme file here][3] then double-click the downloaded file to install it.

One problem with the default Markdown preferences in TextMate 2 is that it uses a horrible font. So I created a new set of preferences in a bundle to override these and make headings use the `Menlo` font instead of `Baskerville`. This bundle is available at [https://github.com/hiltmon/hiltons-bundle][4] and the installation instructions are in the `README` file.

## Bundles

{% img right /images/textmate-auto-lang.jpg 350 231 %}

One of the benefits of TextMate 2 over Sublime Text 2 is that adding new bundles, themes and languages is all built-in, you do not need a third party package manager. The first time TextMate 2 encounters a file it does not recognize, it gives you the option to download and install the bundle for it.

You can manually choose the bundles you want to start with by going into **TextMate / Preferences…** or typing `⌘,` and switching to the **Bundles** tab. Some bundles I really like include:

- **CSS**, **HTML** and **JavaScript** for web work,
- **Ruby**, **Ruby on Rails**, **CoffeeScript**, **JavaScript**, **JSON**, and **YAML** which is where TextMate has traditionally excelled,
- **Git** for source code control,
- **Shell Script** for all my automation,
- **TODO** to track and show TODO comments,
- My **Gists** bundle to integrate with Github Gists,
- And of course, **Markdown** for writing.

## Properties

You don't really need to do anything else. TextMate 2 automatically saves your global, font, theme and language specific preferences as you set them. Whenever you go back to a file, the preferences are just there.

But if you really do want to tweak TextMate 2 even more, you can create a `.tm_properties` in your home folder for global settings and a `.tm_properties` file at the root of each project for project specific settings.

My global `.tm_properties` is this:

```
# Settings

encoding         = UTF-8
fontName         = "Menlo"
fontSize         = 12
lineEndings      = '\n'
showInvisibles   = false
softWrap         = true
tabSize          = 2

# Now using CombinedCasts theme (of course)

theme            = 570BB45C-486D-44A6-8683-CFE4F63CE651

# Hide log, vendor and tmp directories from search popups.

myExtraExcludes = "log,vendor,tmp"
excludeInFileChooser  = "{$excludeInFileChooser,$myExtraExcludes}" 
excludeInFolderSearch = "{$excludeInFolderSearch,$myExtraExcludes}" 
fileBrowserGlob  = "{*,.tm_properties,.htaccess}"

# Variables

PATH   = "$PATH:$HOME/Scripts"
TM_GIT = "/usr/bin/git"
TM_RUBY = "/Users/Hiltmon/.rvm/bin/rvm-auto-ruby"

[ text ]
spellChecking    = true
softWrap         = false
wrapColumn       = "Use Window Frame"
softTabs         = true
tabSize          = 2

[ text.plain ]
spellChecking    = true
softWrap         = true
wrapColumn       = "Use Window Frame"
softTabs         = false
tabSize          = 4

[ text.html.markdown ]
spellChecking    = true
softWrap         = true
wrapColumn       = "Use Window Frame"
softTabs         = false
tabSize          = 4

[ source ]
softWrap         = true
wrapColumn       = "Use Window Frame"
softTabs         = true
tabSize          = 2

[ source.plist ]
softTabs       = false
tabSize        = 4

[ source.tm-properties ]
spellChecking  = false

[ "{Capfile,Gemfile,Gemfile.lock,Guardfile}" ]
fileType         = source.ruby

[ Procfile ]
fileType         = source.yaml
```

This mostly sets tabs and spaces for the most common languages that I use, as well as forces a reset of the theme and font whenever I load the application.

For the [Kifu][kifuapp] project, I have a `.tm_properties` in its root containing:

```
projectDirectory = "$CWD"
windowTitle      = "$TM_DISPLAYNAME — Kifu App (git: $TM_SCM_BRANCH)"

TM_ORGANIZATION_NAME = 'Noverse LLC'

[ attr.untitled ]
fileType         = source.ruby.rails
```

This shows the Git branch in the title bar and assumes all blank files are rails files.

## Works for Me

I also run the file browser to the right, have Software Update set for `Nightly Builds`, show command output in a new window and use the `rvm` version of ruby from my [RVM in TextMate 2][5] post.

With these minor changes, I feel I have the best programmer's editor environment in TextMate 2 *for my own needs* and use it every single day.

See also: [TextMate 2 Basics]({{ root_url }}/blog/2013/11/09/textmate-2-basics/)

*Follow the author as [@hiltmon][twitter] on Twitter and [@hiltmon][app] on App.Net. Mute `#xpost` on one.*

[1]:	https://hiltmon.com/blog/2012/08/14/my-sublime-text-2-setup/
[2]:	https://hiltmon.com/blog/2013/02/22/multiple-themes-in-textmate-2/
[3]:	https://hiltmon.com/files/CombinedCasts.tmTheme
[4]:	https://github.com/hiltmon/hiltons-bundle
[5]:	https://hiltmon.com/blog/2013/01/16/rvm-in-textmate-2/

[app]: http://alpha.app.net/hiltmon
[github]: https://github.com/textmate/textmate
[kifuapp]: http://www.kifuapp.com
[sublimetext]: http://www.sublimetext.com/2
[twitter]: http://twitter.com/hiltmon