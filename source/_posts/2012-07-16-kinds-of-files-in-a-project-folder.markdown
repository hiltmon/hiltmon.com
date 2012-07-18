---
layout: post
title: "Kinds of Files in a Project Folder"
date: 2012-07-16 12:47
comments: true
categories: 
---

In preparation for a client call, I wrote a quick and dirty script to count the kinds of files in a project folder to show them what's involved. I wanted a nice presentation, and the files grouped into categories. I also added parameters to *exclude* certain folder patterns from the counter.

The command is 

``` sh
$ ~/Scripts/cfile.rb ~/Projects/Kifu/code/kifu log tmp doc versions
```

The output is

```
Project File Counter v0.1 ©hiltmon.com 2012 http://www.hiltmon.com

Project: kifu
-------------------------------------------------------
Text Files:
    Markdown              :      1
    Plain Text            :      1
-------------------------------------------------------
Code Files:
    CoffeeScript          :      7
    CSS                   :     10
    ERB                   :    251
    HTML                  :      3
    JavaScripts           :     10
    Ruby                  :    265
    SCSS                  :     10
-------------------------------------------------------
Data Files:
    XML                   :      1
-------------------------------------------------------
Image Files:
    GIF Images            :      2
    Icon Images           :      1
    PNG Images            :    168
-------------------------------------------------------
Configuration Files:
    Configuration         :      3
    Rackup                :      1
    YML                   :      4
-------------------------------------------------------
Other Files:
    Unknown Kind          :      6
    .eot files            :      2
    Locks                 :      1
    Rake                  :      8
    .rdb files            :      1
    Fonts                 :      4
-------------------------------------------------------
TOTAL                     :    760 Files
-------------------------------------------------------
```

It aint pretty, as it was written very quickly. The script in a [gist](cfile.rb) is:

{% gist 3123720 cfile.rb %}
