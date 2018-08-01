---
layout: post
title: "Octopress now has Footnotes"
date: 2013-05-08 17:30
comments: true
categories: [ Octopress ]
---

If you update to the latest Octopress and you still use the `rdiscount` markdown processor, you now get footnotes like this [^1].  <span class="light">I was previously using a CSS workaround because I prefer the speed of `rdiscount` for my growing site[^2] and still wanted footnotes.</span>

To create a footnote, use the standard MultiMarkdown `[^1]` anchor to create the footnote reference link, and add `[^1]: The footnote content.` to the bottom of the file[^3].

I also prefer my footnotes a tad smaller, lighter and closer together, so I added the following CSS to my `sass/custom/_styles.css` file:

``` sass
.footnotes {
  font-size: 13px;
  line-height: 16px;
  color: #666;
  
  p {
	  margin-bottom: 6px;
  }
}
```

If you prefer popover style footnotes (which I do not), try the [Footnotes Popover](https://github.com/mattgemmell/footnotes-popover) by [Matt Gemmell](http://mattgemmell.com).

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[^1]: This is a footnote.
[^2]: If you had changed Markdown processors, you would have gotten footnotes sooner, but at the cost of significantly slower site generation speed. `rdiscount` is fast C code, the others are slower interpreted code.
[^3]: **Bold** and *italics* work here too.