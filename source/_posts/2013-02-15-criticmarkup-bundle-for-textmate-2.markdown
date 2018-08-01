---
layout: post
title: "CriticMarkup Bundle for TextMate 2"
date: 2013-02-15 12:38
comments: true
categories: [ TextMate, Markdown, Text Editors ]
---

> ***Update**: Christian Tietze ([@DivineDominion](http://twitter.com/DivineDominion)) has created a bundle that's included in the official toolkit, so I contributed my bundle's commands to that, and will be using and contributing to that one from now on. Get the full toolkit at [CriticMarkup-toolkit](https://github.com/CriticMarkup/CriticMarkup-toolkit) or just the TextMate bundle at [criticmarkup.tmbundle](https://github.com/DivineDominion/criticmarkup.tmbundle). I've already taken my repo down to prevent confusion.*

Recently, [@macdrifter](http://twitter.com/macdrifter) and [@themindfulbit](http://twitter.com/themindfulbit) announced [CriticMarkup](http://criticmarkup.com), a way for authors and editors to track changes to documents in plain text. I created a [TextMate 2](http://blog.macromates.com/2012/textmate-2-at-github/) bundle to add this markup to *my* favorite text editor for [Markdown](http://daringfireball.net/projects/markdown/) files.

<iframe width="640" height="480" src="http://www.youtube.com/embed/R43p-VjS__I?rel=0" frameborder="0" allowfullscreen></iframe>

Currently, the bundle implements the usual `Markdown` functionality, plus the five [CriticMarkup](http://criticmarkup.com) tags:

* Addition `{++ ++}` (⇧⌘A)
* Deletion `{-- --}` (⇧⌘D)
* Substitution `{~~ ~> ~~}`(⇧⌘S)
* Comment `{>> <<}` (⇧⌘/)
* Highlight `{== ==}{>> <<}` (⇧⌘H) (*Bundle updated 2013-02-15, did not update the video*)

<del>It also contains the Critic theme used in the demo.</del>

<del>You can download and install the bundle from [https://github.com/hiltmon/Critic-Markup.tmbundle](https://github.com/hiltmon/Critic-Markup.tmbundle). Let me know what you think via [GitHub](https://github.com/hiltmon/Critic-Markup.tmbundle/issues) or [Twitter](https://twitter.com/hiltmon).</del>

<del>**This is at best beta-level software (my first public bundle) and has been tested and run on one and only one machine, mine with one version of TextMate, TM2! You takes your chances by installing it.**</del>

Enjoy.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*