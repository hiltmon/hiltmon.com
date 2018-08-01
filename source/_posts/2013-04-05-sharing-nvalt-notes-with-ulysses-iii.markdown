---
layout: post
title: "Sharing nvAlt Notes with Ulysses III"
date: 2013-04-05 10:49
comments: true
categories: [ Tips and Tricks, Text Editors ]
---

I'm testing out [Ulysses III][linksynergy] for writing and so far I am finding it postively interesting *for a 1.0 rewrite*. One thing I wanted to try was to use it for notes alongside [nvAlt][brettterpstra].

**Here's how to share notes between [Ulysses III][linksynergy] and [nvAlt][brettterpstra].**

{% img right /images/ulysses-one.png 202 138 %}

In [Ulysses III][linksynergy], click the plus icon on the bottom left (1) and choose `Add External Source...` (2). Choose the folder in [Dropbox][dropbox] where you store your [nvAlt][brettterpstra] plain text notes, then click `Open`. *Note that if you just drag and drop your [nvAlt][brettterpstra] folder into [Ulysses III][linksynergy], it will copy all the notes, not reference them.*

In my case, I store my [nvAlt][brettterpstra] notes as plain text files in my `~/Dropbox/Notational Data` folder. As you can see, [Ulysses III][linksynergy] picks this as a [Dropbox][dropbox] folder (with the cloud icon) and displays all your notes as *sheets*.

{% img /images/ulysses-two.png 718 325 %}

[Ulysses III][linksynergy] also displays (and sets) the file name in a *special* comment line at the top starting with `@: `. {% img right /images/ulysses-four.png 189 246 %} When you create a new [Ulysses III][linksynergy] sheet in this folder, you need to set the file name there (or use your [TextExpander shortcuts][hiltmon]).

More Tips:

* Make sure that `.md` is a recognized extension in [nvAlt][brettterpstra] / **Preferences** / **Notes** / **Storage** because that's what [Ulysses III][linksynergy] uses.

* {% img right /images/ulysses-three.png 289 105 %} In [Ulysses III][linksynergy], right click on your notes folder and choose `Edit...`. Check `Always assume Markdown syntax`. That way, all your [nvAlt][brettterpstra] notes will render and edit properly.

More on [Ulysses III][linksynergy] will follow as I continue to test out the product.

*Follow the author as [@hiltmon][twitter] on Twitter and [@hiltmon][app] on App.Net. Mute `#xpost` on one.*

[app]: http://alpha.app.net/hiltmon
[brettterpstra]: http://brettterpstra.com/projects/nvalt/
[dropbox]: https://www.dropbox.com
[hiltmon]: https://hiltmon.com/blog/2012/04/15/text-notes-going-electronic/
[linksynergy]: https://itunes.apple.com/us/app/ulysses-iii/id623795237?mt=12&uo=4&at=10l894
[twitter]: https://twitter.com/hiltmon