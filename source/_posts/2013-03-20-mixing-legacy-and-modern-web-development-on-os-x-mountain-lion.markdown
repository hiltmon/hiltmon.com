---
layout: post
title: "Mixing Legacy and Modern Web Development on OS X Mountain Lion"
date: 2013-03-20 16:42
comments: true
categories: [ Development, Productivity, Tips and Tricks ]
---

Over the past few years I have been developing *modern* web applications like [Kifu][kifuapp] on my laptop using [Ruby on Rails][rubyonrails], [Sinatra][sinatrarb], [Octopress][octopress], and [Node.js][nodejs] powered by [Pow][pow]. But over the next few weeks I'll be helping a friend upgrade a bunch of older legacy static (plain HTML), [PHP][php] and [Wordpress][wordpress] sites.

I *do* want to keep using the same smooth workflow processes as I have now. But I do *not* want to clutter up my pristine OS X installation to do it. So this is how I have my *modern* web development environment set up, and how I have added *almost seamless* legacy development capability to it.

<!--more-->

*If you want to skip the details and see how to set up [Pow][pow] and Apache on OS X Mountain Lion to work together, <a href="#fast">click here</a>.*

## My Modern Web Development Setup

The *modern* platform is:

* [PostgreSQL][postgresql] is my development database because that's what all my production databases are. But instead of using the [Homebrew][github] or a native install (and therefore having it running when I do *not* need it), I run the [Postgres.app][postgresapp] by Matt Thompson at Heroku. This app starts a PostgreSQL server instantly on launch and stores it in `~/Library/Application Support`. I have a [Keyboard Maestro][linksynergy] macro set up on ⇧⌃⌥⌘P to start and kill this app when needed<a href="#fn:1" id="fnref:1"><sup>[1]</sup></a>.
* I use [Pow][pow] as my development web server because all my modern web sites are Rack apps. Pow is great because it *just works* by intercepting DNS requests and automatically redirecting you to your development web servers on the `.dev` domain (no more `/etc/hosts` hacks needed, still pristine). Just follow [the link][pow] to install [Pow][pow] and see how to symlink sites to activate them. I also created Safari bookmarks for each and every `.dev` site I work on so I can easily get to them for demo or development purposes.
* I use [rvm][rvm] to manage the versions of ruby and the gemsets I need for each project (and it works automatically with [Pow][pow]).
* I use the [foreman][github 2] gem to launch and manage additional services needed, such as [redis][redis], worker threads and a development web server.

So, lets say I want to **work** on [Kifu][kifuapp]. I have a [Keyboard Maestro][linksynergy] macro that does the following:

* Starts [Postgres.app][postgresapp] if it is *not* already running.
* Opens a new [iTerm 2][iterm2] session, and `cd`'s to the Kifu folder.
* Kicks off a [TextMate 2][github 3] session with the Kifu code in it.
* Opens a second terminal tab and kicks off [foreman][github 2] so all the services needed start up.
* Launches a new web browser window that takes me to the development site.
* Triggers [Moom][linksynergy 2] to place all the windows where I want them (I'm still old school spatial).

If I want to **demo** Kifu, I just have to start [Postgres.app][postgresapp] with ⇧⌃⌥⌘P and launch a browser.

Done with that, and want to blog? Another macro kills off the development environment leaving me with a *clean* system.

A key benefit of the *modern* setup is since my blog is an [Octopress][octopress] site, I can always view it locally via [Pow][pow] - it does not need a database running. While writing, I leave a `rake watch` running in a terminal. Easy.

So my *modern* environment relies on [Pow][pow] for serving most pages and [Keyboard Maestro][linksynergy] macros to start and stop what I need. Its quick to start up, and does not chew up resources when I do not need it.

## Enabling Legacy 

The legacy sites I *will* be working on need a few things my current environment does not support:

* A [MySQL][mysql] database for [Wordpress][wordpress]
* A server to process [PHP][php] ([Pow][pow] does not do PHP)

[MAMP][mamp] is the platform most developers use on OS X when they need to deal with MySQL or PHP because it's *easy* to set up, *easy* to start and *easy* to use. 

But it does *not* work for me. *Here's why*:

1. First, both Apache and PHP are already installed on OS X and I do not want to have to launch something else just to *demo* a site. I am spoilt by Pow.
2. Secondly, if you are working on more than one site, you need to purchase and install the Pro version of [MAMP][mamp].
3. Thirdly, I deleted [MAMP][mamp] once before and forgot that I had a valuable database in it's folder, ouch! 

For my needs, it's just easier to bite the bullet and run a local MySql Server *when* I need it.

Since there is no app for [MySQL][mysql] like [Postgres.app][postgresapp], I installed the latest [MySql 64-bit Mac version][mysql 2] directly from MySQL. Choose the `DMG` version to download and hit "No thanks, just start my download." to bypass the Oracle sign-up irritant. The reason you want the `DMG` version is that it contains an installer for the database - which makes it easy to install - and the Preference Pane to manage it - double click to install that. I did *not* install the Startup Item because I only want MySQL running when I need it (just like PostgreSQL). If you are doing this on a desktop computer, by all means set that up too.

Since Apache and PHP is already installed, we just have to start it. And ...

Wait, what? Really, Apple, really?

Under previous versions of OS X, the option to start and stop Apache was in **Preferences.app** / **Sharing**. But that was **removed** in OS X Mountain Lion. *Whomever the lowlife at Apple is who decided to remove it shall face my wrath if and when I ever meet them (or needs to bribe me with excellent scotch to stop whining about it)*.

One solution to this lunacy is to purchase and install OS X Server which kindly gives you limited access to the Apache startup and a full PostgreSQL database install, but this is a development laptop, I don't need all that running all the time. Another is to install the [Web Sharing Prefpane][clickontyler] by Tyler Hall; but I did not do this, it feels too much like a hack.

The third option is to use the terminal to start Apache:

	sudo apachectl restart
	
The *good* part about this is that OS X *remembers* that you started Apache before and does so again on the next reboot. No need to run this command again.

But with [Pow][pow] installed, how do you access Apache and PHP for *legacy* work since Pow redirects *all* local web requests to it's own server for *modern* work? I configured the [37signals][37signals] trick to serve *legacy* from Apache and *modern* from Pow.

*Aside: I did try using `Rack::Legacy` to convert *legacy* apps into rack apps that Pow can serve, but I hated that you have to build your own PHP stack to access the commands needed. And I failed to get it working anyway.*

## <a name="fast"></a>Making Pow and Apache work together

You can find the *37signals trick* details at [Running Pow with Apache][github 4], but they gloss over a few issues and steps that I cover in more detail here.

Run the following commands as per the trick, one after the other  <span class="light">(you uninstall Pow, reconfigure it, reconfigure Apache, reinstall Pow)</span>:

	$ curl get.pow.cx/uninstall.sh | sh #if you have pow installed
	$ echo 'export POW_DST_PORT=88' >> ~/.powconfig
	$ sudo curl https://raw.github.com/gist/1058580/zzz_pow.conf -o /private/etc/apache2/other/zzz_pow.conf
	$ sudo apachectl restart
	$ curl get.pow.cx | sh

If you try your *modern* sites now (in my case, say `http://hiltmon.dev`), they should still work. Pow still takes over the DNS handling of the `.dev` domain, but now it redirects all calls to Apache, which then passes them through to the Pow web server. A smidge slower performance, but it works.

Time to set up the legacy sites. We need to tell Apache to serve these and *not* pass them through.

Create a file in `/etc/apache2/other` called *yoursite*.conf (where *yoursite* is the site name). For example, I have a `testwordpress` site so the file name is `testwordpress.conf`. Then add the following text to it:

``` xml
<VirtualHost *:80>
    DocumentRoot /Users/Hiltmon/Projects/Wordpress/code/testwordpress
	ServerName testwordpress.dev

    <Directory "/Users/Hiltmon/Projects/Wordpress/code/testwordpress">
        Options Indexes FollowSymLinks
	    AllowOverride All
    	Order allow,deny
      	Allow from all
	</Directory>
</VirtualHost>
```

Replace `/Users/Hiltmon/Projects/Wordpress/code/testwordpress` with the path to the root of your legacy site and make sure that the `ServerName` matches the `.dev` domain you would like to use.

Then start MySQL and restart apache

	$ sudo /usr/local/mysql/support-files/mysql.server start
	$ sudo apachectl restart
	
If you go to your *legacy* `.dev` path from your browser (in my case `http://testwordpress.dev`), you should get the *legacy* site back. Apache and PHP are happily serving it. Try a *modern* `.dev` path (`http://hiltmon.dev` again), and after a tick, it should come up too as Pow serves it. Brilliant!

To make this work for me the same as *modern* development, I created a [Keyboard Maestro][linksynergy] macro on ⇧⌃⌥⌘O to start and stop MySQL<a href="#fn:2" id="fnref:2"><sup>[2]</sup></a>. I leave Apache running like Pow, it does not use any resources when not in use.

Note that:

* These *legacy* sites do not need to be in `public` folders like rack apps as they are plain old web sites.
* If you get an error from Apache, it's usually permissions, but check the following:
	* `chmod 755` all the folders in the path to the legacy site root
	* Check the path in the `.conf` file is correct and restart Apache
	* Make sure your `.conf` file is not lexically after `zzz_pow.conf`
	* Make sure that `NameVirtualHost *:80` is uncommented in `/etc/apache2/extra/httpd-vhosts.conf`.
* Because its read-only for Apache, the Wordpress installer cannot write the `wp-config.php` file, but if you're doing this, I'm sure you can cope.

## Modern and Legacy Together

As a result of all this hackage, I can now develop and demo both *modern* and *legacy* web sites on my laptop reliably using the same flows and tools I prefer by triggering a different set of keyboard macros. And then kill off unnecessary services when I no longer need them with more macros. All without cluttering up OS X outside my home folder too much and without fear that I'm going to delete any key databases.

Now to see if I remember any PHP!

*Follow the author as [@hiltmon][twitter] on Twitter and [@hiltmon][app] on App.Net. Mute `#xpost` on one.*

---
<div class="footnotes">
    <ol>
        <li id="fn:1">The Keyboard Maestro Macro to toggle <strong>Postgres.app</strong> is on the left.<a href="#fnref:1" title="Back to Post"><sup>&#160;&#8617;</sup></a></li>
        <li id="fn:2">The Keyboard Maestro Macro to toggle <strong>MySQL</strong> is on the right. <strong>Replace the `sudo ...` in each script line with `echo myPassword | sudo -S ...` to make it work.</strong><a href="#fnref:2" title="Back to Post"><sup>&#160;&#8617;</sup></a></li>
    </ol>
</div>

{% img /images/toggle-databases.jpg 700 579 %}

[37signals]: http://37signals.com
[app]: http://alpha.app.net/hiltmon
[clickontyler]: http://clickontyler.com/blog/2012/02/web-sharing-mountain-lion/
[github]: http://mxcl.github.com/homebrew/
[github 2]: https://github.com/ddollar/foreman
[github 3]: https://github.com/textmate/textmate
[github 4]: https://github.com/37signals/pow/wiki/Running-Pow-with-Apache
[iterm2]: http://www.iterm2.com/#/section/home
[kifuapp]: http://www.kifuapp.com
[linksynergy]: http://www.keyboardmaestro.com/main/
[linksynergy 2]: http://manytricks.com/moom/
[mamp]: http://www.mamp.info/en/index.html
[mysql]: http://www.mysql.com
[mysql 2]: http://dev.mysql.com/downloads/mysql/
[nodejs]: http://nodejs.org
[octopress]: http://octopress.org
[php]: http://php.net
[postgresapp]: http://postgresapp.com
[postgresql]: http://www.postgresql.org
[pow]: http://pow.cx
[redis]: http://redis.io
[rubyonrails]: http://rubyonrails.org
[rvm]: https://rvm.io
[sinatrarb]: http://www.sinatrarb.com
[twitter]: http://twitter.com/hiltmon
[wordpress]: http://wordpress.org