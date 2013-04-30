---
layout: post
title: "Octopress Post and Publish"
date: 2012-07-18 18:01
comments: true
categories: [Productivity, Octopress]
---

Since this site is getting larger and it's running on [Octopress](http://octopress.org), the `rake generate` and `rake preview` processes are getting slower. Enter `rake isolate["x"]` to isolate the site down to the selected post. But isolating requires me to note the file name down, there is too much to remember and type and I am lazy.

So have created two macros and a script to speed this process up.

**Note: You must run these commands in the root of the Octopress folder, else they will not work at all!**

## Post

### The old, standard way

To create a post in Octopress, isolate it and preview it in the browser, you need to run the following steps:

Create the Post:

``` sh
$ rake new_post["Octopress Post and Publish"]
```

Isolate the post using the generated file name:

``` sh
rake isolate["octopress-post-and-publish"]
```

And generate and start the preview thread:

```sh
rake generate
rake preview
```

Note that I have already hacked the `new_post` function in my Rakefile to also log this to [Day One](http://dayoneapp.com) and launch [Byword](http://bywordapp.com), see my post on [Bread Crumbs in Day One](http://hiltmon.com/blog/2012/01/23/bread-crumbs-in-day-one/), so those steps are not shown.

### The new way

For this post, I typed in:

```sh
$ post Octopress Post and Publish
```

Note that there is no punctuation after the `post` command, less for me to type. The script concatenates all parameters into a single title string. The result of the command shows that it does all the steps I did manually, including figuring out the file name, and leaving me in a preview thread:

``` text
:: rake new_post["Octopress Post and Publish"]
mkdir -p source/_posts
:: rake isolate["octopress-post-and-publish"]
:: rake generate
:: rake preview
[2012-07-18 18:01:34] INFO  WEBrick 1.3.1
[2012-07-18 18:01:34] INFO  ruby 1.9.2 (2011-07-09) [x86_64-darwin11.2.0]
[2012-07-18 18:01:34] INFO  WEBrick::HTTPServer#start: pid=35734 port=4000
```

## Publish

### The old, standard way

I would use `^C` to stop the preview thread, then:

``` sh
$ rake integrate
$ rake gen_deploy
```

### The new way

Now I just use `^C` to stop the preview thread, and:

``` sh
$ publish
```

## The macros and scripts

I created the following ruby script to handle the post function. If you want the "Open in Byword" function, uncomment Line 29: `open "#{path}" -a Byword` (Untested)

{% gist 3139294 post.rb %}

I then added the following two macros to my `.bash_profile` (OS X users only). Note that I keep all my custom scripts in `~/Scripts/`:

``` sh
function post {
  ~/Scripts/post.rb $*
}

function publish {
  rake integrate
  rake gen_deploy
}
```

These work for all my Octopress sites. It allows me to get to the post faster, preview that it looks right and publish the site with ease.
