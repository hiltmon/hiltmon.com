---
layout: post
title: "Bread crumbs in Day One"
date: 2012-01-23 13:09
comments: true
categories: Productivity
---

I switched over to [Day One](http://dayoneapp.com/) for journaling at the start of the year on a lark, and its become a core part of my process.

Here are three things I do with it:

### 1. Bread crumb blog posts

I have updated the Octopress `rake` file for `new_post` to also bread crumb the new post in [Day One](http://dayoneapp.com/) (and launch [Byword](http://bywordapp.com/) for editing).

Place this at the end of the `:new_post` task (see below for details on the `LogToDayOne.rb` script)

``` ruby
  # Log to Day One and open it for editing
  %x{~/scripts/LogtoDayOne.rb "@blog #{title}"}
  %x{open "#{filename}"}
```

The first line runs the `LogToDayOne.rb` passing in the blog title. The second line opens the generated markdown file using the default editor (of course [Byword](http://bywordapp.com/) is it).

Here it is in [Day One](http://dayoneapp.com/):

{% img /images/day-one-sample-1.png 291 120 %}

### 2. Log all commits

I have created a shell macro to log all git commits such that the project and commit message is also logged to [Day One](http://dayoneapp.com/).

In `.bash_profile`:

``` sh
function gca(){
  msg=$*
  path=$(pwd)
  ~/scripts/LogtoDayOne.rb "@${path##*/} $msg"
  git commit -am "$msg"
}
```

Now all I do is type `gca "The commit message"` and its both logged to [Day One](http://dayoneapp.com/) and saved in git.

Here it is in [Day One](http://dayoneapp.com/):

{% img /images/day-one-sample-2.png 368 64 %}

### 3. Use the annoying reminders

I have enabled the reminders function in [Day One](http://dayoneapp.com/) so that 3 times a day, an annoying gray box comes up asking me to journal something. So I do. And its been totally worth it.  There is always something to note, something to remember, something to write about. Even though I have only been doing this a month, I can already see a clear journal of my activities in [Day One](http://dayoneapp.com/).

### The script

Logging commits was not my idea. I got the `LogToDayOne.rb` script from Brett Terpstra in [Logging with Day One, Geek Style](http://brettterpstra.com/logging-with-day-one-geek-style/) - and removed the dependency on `chronic` since I do not need it and it was conflicting with the RVM in Octopress. I though it was so cool, I added the blog bread crumb myself in Octopress.

### The result

As a result of these, I have a comprehensive journal of what happened each day over and above my project and coding notes.

Anyone else got some cool scripts for [Day One](http://dayoneapp.com/)? I'd love it to become more like [Momento](http://www.momentoapp.com/) for the Mac.


