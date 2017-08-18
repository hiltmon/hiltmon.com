---
layout: post
title: "Download Dreamhost Server Logs"
date: 2013-02-10 14:38
comments: true
categories: [ Web ]
---

This site is hosted on [Dreamhost](http://www.dreamhost.com/r.cgi?258997), and I could not be happier with them. But some time ago, the engineers there decided to disable FTP access to the server logs. No reason given.

If you have a Dreamhost shared account, try it. `ftp` into your server using your favorite FTP client, click the `logs` folder, then your site folder, then  `http` and you’ll get an error. This is because the `http` folder is actually a symlink to a private, readonly folder on the server that is inaccessible to FTP. If you `ssh` in, you can `cd` to this folder and see the logs because the shell *can* traverse this symlink.

To download your logs, just use the `scp` command locally in your terminal as follows:

``` sh
scp <user>@<domain>:/home/<user>/logs/<domain>/http/* <local-path>
```

Where

* `<user>` is your Dreamhost shell user name
* `<domain>` is your hosting domain name, and
* `<local-path>` is where you want to dump the files

Note that I have no password in the command as I have set up [ssh keys](http://wiki.dreamhost.com/SSH).

I use:

``` sh
scp hiltmon@hiltmon.com:/home/hiltmon/logs/hiltmon.com/http/* ~/Projects/HiltmonDotCom/data/logs/
```

This command downloads all my logs into the correct place in my [standard project folders](https://hiltmon.com/blog/2012/06/30/project-folder-layout/). Note that Dreamhost only keeps about five (5) days of logs, so do this every few days to get it all.

Lovely!

*Geek Aside: I rarely use this, I get all my stats from Google Analytics, but do occasionally check the `errors.log` file which is how I found that I was missing the [web clip icons](https://hiltmon.com/blog/2013/02/10/add-web-clip-icons-to-octopress/).*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
