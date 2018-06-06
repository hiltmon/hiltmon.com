---
layout: post
title: "Laravel 4 Blade TextMate Bundle"
date: 2013-07-28 11:37
comments: true
categories: [ Productivity, TextMate ]
---

In the [comments](https://hiltmon.com/blog/2013/04/15/my-textmate-2-setup/#comment-973665378) of [My TextMate 2 Setup](https://hiltmon.com/blog/2013/04/15/my-textmate-2-setup/#comment-973665378), reader Bob Rockerfeller wondered if the [Sublime Text Laravel 4 Blade bundle](https://github.com/Medalink/Laravel-Blade) could be ported to TextMate 2. So I did.

It was easy because Sublime Text uses TextMate's `.tmLanguage` file format for syntax highlighting. I just created a new bundle using the Bundle Editor, created a new Syntax file and pasted in Eric Percifield's ([@medalink7](https://twitter.com/medalink7)) code. Then tested it with the example in his repo.

You can download the bundle here: [Laravel Blade.tmbundle](https://hiltmon.com/files/Laravel-Blade.tmbundle.zip).

**To Install:** Unzip the file and double-click the `Laravel Blade.tmBundle` icon to have TextMate install it for you. Alternatively, drag and drop the `Laravel Blade.tmBundle` to `~/Library/Application Support/Avian/Bundles/` folder.

Enjoy.

**Disclaimer: I don't use Laravel, I just use TextMate 2. All the good work in this bundle was done by [@medalink7](https://twitter.com/medalink7), thank you,  I just packaged it into a TextMate bundle format.**

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
