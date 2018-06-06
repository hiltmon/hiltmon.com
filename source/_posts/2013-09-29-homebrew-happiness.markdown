---
layout: post
title: "Homebrew Happiness"
date: 2013-09-29 12:12
comments: true
categories: [ development, macintosh, unix, tips and tricks ]
---

<span class="light">*If you are expecting an article about beer, this is not it. This is about the best product that helps install and manage the Open Source software on the Macintosh computer that Apple decided not to include in OS X.*</span>

In short, I use a lot of Open Source products for work, like [postgresql][pg], [redis][redis], [mongo][mongo], [node][node], [boost][boost] libraries and [rbenv][rbenv]. Installing and managing them natively on a Mac was a pain. [Homebrew][brew] makes installing and maintaining these easy, safe and pleasant without messing up my system. <span class="light">To skip the fascinating introduction and get to the information about the product directly, click [Take me to Homebrew Happiness](#hh).</span>

### Before Homebrew

Since OS X is really a Darwin flavored FreeBSD UNIX, which is pretty much [Linux Standard Base][LSB] compliant, installing Open Source software on it was never really that hard. The recipe is as easy as a frying an egg:

| Step  | Command |
| ----- | ------- |
| 1. Download the tar file |  `curl -O <path to source tarfile>`
| 2. Unpack it | `tar zxvf <downloaded file>`
| 3. CD to it | `cd <unpacked folder>`
| 4. Configure it | `./configure --prefix=/usr/local`
| 5. Make it |  `make`
| 6. Install it |  `sudo make install`
	
Most Open Source packages just worked. *But many did not.* They may have needed some dependencies to be installed first or the *configure* needed special settings to work. Fortunately, the internet was full of fine folks who tried and created findable pages that explained the dependencies or settings. Follow their recipes, and you could too.

*And that is the way I installed and maintained Open Source packages in my Mac for a decade.*

#### Aside: MacPorts and Fink

Two major projects sprang up to solve for this mess, [MacPorts][Macports] and [Fink][Fink]. They took the standard recipe or the tweaked ones and make easy-to-use to use installers for Mac. They did became very popular, to the point that tweaked recipes started to become scarce.

But I did not use them. 

I tried both, for a while. But while I may be a messy person in real life, I am OCD tidy on my computer. And both of these projects would basically mess up my system. They'd install products in non-standard locations, and leave a mess when removing products. Which meant that when I tried new things on my OS X install, sometimes things that should have worked did not because of this mess. In my humbly correct opinion, `/opt` is not where you install core products. So I blew my machine away and went back to native build and installs.

### The Negative of Native

Native installs meant I always used the vendor or developer's version of the code (which was good) and installed it where I wanted it to go. But that too led to other messes.

* Updates were a pain. Not all Open Source products would overwrite older versions cleanly. And updates often relied on undocumented dependency updates which led to install hell.
* The installation process was time consuming. Download, *wait*, unpack, configure, *wait*, make, *wait*, install, *wait*. And that assumes it all worked the first time. Usually the *configure* step would fail and then time needed to be spent figuring out what setting to change or dependencies to install.
* Products that depended on the products I natively installed would often make assumptions about the location of the dependency, making their installs more hairy too.
* Matching the server versions of products was nasty. I run [CentOS][centos] on all my servers and the `yum` install for each Open Source product was simple and easy, not so much when you do it yourself.
* And half the time I would have no idea what was installed and where it was on my system.

### <a name="hh"></a>Homebrew Happiness

Enter [Homebrew][brew] by "Splendid Chap" [Max Howell][max] stage left.

It solves *all* the problems mentioned above, including:

* Dependency management is in each install *formula*, so dependencies get installed automatically, by [Homebrew][brew], where they should be.
* The installed applications get installed safely out of the way (but still in `/usr/local`), so the system remains clean, and then symlinked into the right place in `/usr/local` where your deity expects it to be.
* Installs just work.
* Updates just work.
* Removals just work, and leave no mess or trace.

### Using Homebrew

To get started with [Homebrew][brew], you will need a Mac with OS X and Xcode installed (for the developer tools). Then go to the [Homebrew][brew] web site and copy and paste the command into a terminal (or use this)

	ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
	
The installer will explain what it does and set up the [Homebrew][brew] environment. Once it's done, do a

	brew update
	
To ensure all the formulas are the latest. I heartily recommend you do this before any [Homebrew][brew] changes on your system every time.

To install a product, just

	brew install <formula>
	
To see what formulae are available, use:

	brew search
	
If you have an idea what you are looking for, use:

	brew search <formula>

To see what you have installed:

	brew list
	
To update an installed project:

	brew upgrade <formula>

If you ever want to know where the settings files for a project are, just use

	brew info <formula>
	
To cleanly uninstall a project:

	brew uninstall <formula>
	
And if you are OCD clean like me, run this to be sure your [Homebrew][brew] stuff is all *copacetic*:

	brew doctor
	
The only negative I have found is that [Homebrew][brew] does not have *every* Open Source project or product in it. In some cases, the [Homebrew][brew] brewmasters have even removed formulae which were not being used or made no sense. In my case, I use [QuickFix][qf] and the C++ `libmongoclient.a` which I still had to manually install. But this point is really moot as creating a new [Homebrew][brew] formula to install these is child's play.

With [Homebrew][brew], I have an OCD clean Mac OS X installation running all my favorite and necessary Open Source packages in a clean, consistent and reliable way. And I hope I never need to deal with manual build and install madness again.

[Homebrew][brew] is yet another indispensable tool in my Mac toolbox.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[LSB]: http://www.linuxfoundation.org/collaborate/workgroups/lsb
[Macports]:	http://www.macports.org
[Fink]:	http://fink.thetis.ig42.org
[brew]:	http://brew.sh
[max]: http://mxcl.github.io
[pg]: http://www.postgresql.org
[redis]: http://redis.io
[mongo]: http://www.mongodb.org
[node]: http://nodejs.org
[boost]: http://www.boost.org
[rbenv]: https://github.com/sstephenson/rbenv
[qf]: http://www.quickfixengine.org
[centos]: http://www.centos.org

