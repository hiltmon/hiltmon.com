---
layout: post
title: "Assembly Notes"
date: 2013-01-03 11:27
comments: true
categories: 
---

**Assembly Notes** are documentation that a programmer creates to record all the steps they go through when crafting an application, setting up a new server or configuring a new device. The idea is to log all the things they do *and all the commands they type in* so that they can reproduce the process again later. Assembly Notes are personal or project internal, not shared.

I started writing these when I launched [Noverse](http://www.noverse.com), and use them on all projects. I have notes for each step I performed when creating each application, more notes for how all servers are set up and configured and even notes on how the development environments are set up. In my case, I break these up into weekly files by project, store them in my [standard project folder’s](https://hiltmon.com/blog/2012/06/30/project-folder-layout/) Notes folder and use these logs as the source when reporting progress to clients as well.

*By noting everything, you miss nothing. And you have a script to reproduce what you did.*

Assembly notes are different to to-do’s (although they often contain to-do notes). It is a record of what *was* tried, what *was* done, what worked, what did not, and how it all can be reproduced.

## Project Assembly Notes

Here is a sample of the top of one of my Assembly Notes for Kifu (scroll down as it’s quite long):

```
Title:    Kifu Assembly Notes  
Subtitle: Week 38 (Week 45 of Project)  
Author: Hilton Lipschitz  
Affiliation: Noverse LLC  
Web:    http://www.noverse.com  
Date:   March 2, 2012  

# Optimization 

Now that we have a large dataset, need to speed things up. Running performance stats to find the bottlenecks.

BRANCH: optimize-1

- Add TEST to project so I can run benchmarks and profile tests

Here goes

    rails generate performance_test aging_by_event_summary
    
And added the `DevelopmentProfiler` class

Use as

    DevelopmentProfiler::prof("<profile_file_name>") do
      # CODE TO PROFILE
    end
    
## Improvements

Start @36.02

- `aging_by_event_summary`/0.4s: Fewer billings calls and assed `this_bill_` variants
- `aging_by_account_detail`/2.0s: No include phones and emails in query (this will slow down the collections report)
- `import`
    - No validations after saving an allocation /2.0s
    - No validations on creating an attending/1.0s
    - No validations on others/0.8s
    - Move some observers into classes/0.06s @27.31
    - Move more into classes/0.16s @27.15
    - Move more into classes/-.--s @26.44
    - Move all into classes/-.--s @26.20

## TODO

- ✓ Use `this_bill_` variant when getting `Billing` outstanding, payable or allocated
- ☐ `aging_by_account_detail` PDF is 62 seconds after changes (all in the PRAWN module!)

## More

- Fix billing messages
- BUG in parse_date on Event -> all observers need a self tag

- Cleaned up models, removed old observers
- Starting on Controllers

MERGE: develop

## Rename things

BRANCH: rename-1

- ✓ Rename review account and make it more RESTful
- ✓ Rename roll event
- ☐ Rename billings

IN VIEWS:

- ✓ Disable editing on closed events
- ☐ Sort events and some sub-tables in review
```

About these notes:

* They are written as [Markdown](http://daringfireball.net/projects/markdown/) files (using [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) extensions).
* I have [BBEdit](https://itunes.apple.com/us/app/bbedit/id404009241?mt=12&uo=4&at=10l894) running all the time with the current project and week’s Assembly Notes file open.
* I use [Markdown Metadata](https://hiltmon.com/blog/2012/06/18/markdown-metadata/) headers to record the project, week and date of the notes (always a Friday).
* I often copy and paste command lines in to record what was used. And sometimes the data and output too.
* I usually log the branch name in case I need to go back.
* I use [TextExpander](https://itunes.apple.com/us/app/textexpander-for-mac/id405274824?mt=12&uo=4&at=10l894) shortcuts to create the unchecked ☐ and checked ✓ marks against to-do notes. I often create a plan, note it, then check each item off as I go. *These are tactical plans, what I want to achieve in the next few hours.*
* I write release notes in here too, then copy and paste them out into the application and release emails.

## Server Build Notes

Here is an except from another project’s Server Build Notes:

```
## Step 3 - Postgres

As per `http://yum.postgresql.org/howtoyum.php`, edit the repo to exclude their postgres builds.

	cd /etc/yum.repos.d
	
And edit the file appending `exclude=postgresql*` to _[base]_ and _[updates]_

Download the RPM from the above link

On local, from _downloads_

	scp -p pgdg-centos91-9.1-4.noarch.rpm root@client.com:/root/
	
On server

	rpm -i pgdg-centos91-9.1-4.noarch.rpm
	
	yum install postgresql-libs
	yum install postgresql postgresql-server
	
	service postgresql-9.1 initdb
	
NOTE: No need to add IP access as its local only. This will change when we move it to another server.

	service postgresql-9.1 start
	chkconfig --level 345 postgresql-9.1 on
	
	su - postgres
	createuser noverse
	createdb -O noverse reportingdb_production
	
In `/var/lib/pgsql/9.1/data/pg_hba.conf` replace _ident_ with _trust_. 
	
Test after restart to make _trust_ work (as root)

	service postgresql-9.1 stop
	service postgresql-9.1 start
	psql -d reportingdb_production -U noverse

Database is UP!

## Step 4 - Web

### Ruby 1.9.3

On server, as root

	yum install openssl-devel zlib-devel gcc gcc-c++ make autoconf readline-devel curl-devel expat-devel gettext-devel
	
Download [Ruby 1.9.3-p194](http://www.ruby-lang.org/en/downloads/)

On local

	scp -p ruby-1.9.3-p194.tar root@client.com:/root/
	
On server

Install libyaml as per [http://collectiveidea.com/blog/archives/2011/10/31/install-ruby-193-with-libyaml-on-centos/]()

	wget http://pyyaml.org/download/libyaml/yaml-0.1.4.tar.gz
	tar -C /tmp -xzvf yaml-0.1.4.tar.gz
	cd /tmp/yaml-0.1.4
	./configure --prefix=/usr
	make
	make install

Make ruby 

    cd
	tar -C /tmp -xvf ruby-1.9.3-p194.tar
	cd /tmp/ruby-1.9.3-p194/
	./configure --enable-shared --enable-pthread --prefix=/usr
	make -j4
	make install
	
Test
	
	ruby --version
	gem --version
		
OK
```

On build notes:

* I include all dependencies and their installation commands.
* I include all version numbers so I can ‘clone’ the server easily and get the same environment back.
* I explain all decisions, even ones that will change later.
* I include tests to ensure the component works.

## Benefits

One gets a lot of benefit from these including:

* The ability to build a new server quickly as you have a working script to follow.
* The ability to report clearly to clients *all* the work done in a period.
* The ability to go back and see why certain decisions were made.
* The ability to go back and see how things were done, so you can do them again better.
* Documentation on how things were done in other projects so you spend less time doing them in this project.

## Tips and Tricks

I use a lot of snippets to make these. The Assembly Note header is a [TextExpander](https://itunes.apple.com/us/app/textexpander-for-mac/id405274824?mt=12&uo=4&at=10l894) snippet `;mma` that uses fill-ins and a form as follows:

```
Title:          %filltext:name=Project:default=Kifu% Assembly Notes  
Subtitle:       Week %filltext:default=2:width=10% of Project  
Project:        %filltext:name=Project:default=Kifu%  
Author:         Hilton Lipschitz  
Affiliation:    Noverse LLC  
Web:            http://www.noverse.com  
Date:           %B %e, %Y  

```

Which gives:

{% img /images/mmas.jpg 604 221 %}

I also use a [TextExpander](https://itunes.apple.com/us/app/textexpander-for-mac/id405274824?mt=12&uo=4&at=10l894) snippet to break it up into days `;mmd`:

```
---

**%A %B %e, %Y**

```

Which gives me:

```
---

**Thursday January 3, 2013**

```

Finally, I track who reported what using a set of key marks (also [TextExpander](https://itunes.apple.com/us/app/textexpander-for-mac/id405274824?mt=12&uo=4&at=10l894) snippets), and use them in release notes:

* β/HL - `;bm` : Bug Mark (Bug reported by HL)
* ⨍/HL - `;fm` : Feature Mark
* ‽/HL - `;im` : Inquiry Mark (when doing research to answer an inquiry)
* ∁/HL - `;om` : Other Mark (when doing other work for the client or their users)

## It Just Takes Discipline

Creating Assembly Notes and keeping them up to date requires discipline and habit. I *habitually* open [BBEdit](https://itunes.apple.com/us/app/bbedit/id404009241?mt=12&uo=4&at=10l894) and the current project’s Assembly Notes file when I start on a task, just as I habitually kick off the [Billings Pro](https://itunes.apple.com/us/app/billings-pro/id434514810?mt=12&uo=4&at=10l894) timer. And I am *disciplined* enough to use the open notes file to record what I want to get done, paste any notes and thoughts and check them off as I work. It did take a while to get used to working this way, but the benefits of having these process scripts lying around are just too great.

Try creating Assembly Notes from now on, one file a week, and ensure you ALT-TAB to this file when you are between tasks, or thinking or planning or running commands and write what you do. Before you know it, it will become habit and you will have an excellent log to work with.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*