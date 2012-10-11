---
layout: post
title: "Setting up BBEdit for Markdown"
date: 2012-08-03 11:50
comments: true
categories: [Text Editors, Productivity]
---

Two advanced settings are needed to make [BBEdit](http://www.barebones.com/products/bbedit/index.html) treat all *new* documents as Markdown format, and to save with the correct file extension. They are:

``` sh
defaults write com.barebones.bbedit PreferredFilenameExtension_Markdown -string "markdown"
defaults write com.barebones.bbedit DefaultLanguageNameForNewDocuments Markdown
```

If you use [TextWrangler](http://www.barebones.com/products/TextWrangler/), replace the “bbedit” in the above with “textwrangler”. But I’d recommend purchasing BBEdit instead.
