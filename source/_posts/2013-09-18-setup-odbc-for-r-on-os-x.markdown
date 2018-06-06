---
layout: post
title: "Setup ODBC for R on OS X"
date: 2013-09-18 12:59
comments: true
categories: 
---

**Hi Folks, Please do not follow this advice, its an old article that somehow has stayed way past its welcome in the search engines. Use the `RPostgresSQL` package that connects directly using the C drivers, its a lot faster to set up and run. ~Hilton.**

At work, we use [R][rproj] to analyze data and calculate risk. The data is in a [PostgreSQL][postgres] database, so we use the [RODBC][rodbcdl] package to access the database from [R][rproj].

But this does not work under Macintosh OS X.

For two reasons. 

One, it uses the [iODBC][iodbc] libraries that come with OS X and these do not work out of the box. And two, even if you do install the [ODBC Administrator][odbcadmin] tool and configure iODBC, it does not work with unicode drivers and databases.

So here's how to set up [R][rproj] with [unixODBC][unixodbc] on OS X to access a [PostgreSQL][postgres] database.

## Prerequisites

It is assumed you have the following installed and running:

* [Xcode][xcode] with command line tools installed (needed to compile the ODBC drivers and RODBC)
* [R][rproj]
* [RStudio][rstudio] (optional, but so much better than the standard [R][rproj] GUI)
* The database (in my case PostgreSQL, with developer libraries, so that the compiles will work. I installed mine using Homebrew)
* [Homebrew][brew]

## Install unixODBC

This turns out to be easy, just use [Homebrew][brew]:

	$ brew update
	$ brew install unixodbc

## Install the PostgreSQL ODBC Driver

The best way to install this is to download and compile it manually. Download the latest driver file from [the postgres file browser][pgodbc] and then (only commands shown):

	$ tar zxvf psqlodbc-09.02.0100.tar.gz
	$ cd psqlodbc-09.02.0100/
	$ ./configure
	$ make
	$ sudo make install

## Setup the ODBC Driver

Establish the driver in `/usr/local/etc/odbcinst.ini`:

```
[PostgreSQL]
Description     = PostgreSQL ODBC driver (Unicode 9.2)
Driver          = /usr/local/lib/psqlodbcw.so
Debug           = 0
CommLog         = 1
UsageCount      = 1
```

And set up a connection in `/usr/local/etc/odbc.ini`:

```
[ODBC Data Sources]
database1 = My Cool Database

[database1]
Driver      = PostgreSQL
ServerName  = db.domain.local
Port        = 5432
Database    = database1
Username    = hiltmon
Password    = itsasecret
Protocol    = 9.2
Debug       = 1
```

You could also set the connection in `~/.odbc.ini` but I find system level connections work better, especially when moving code into production.

Test the connection using `isql`

	$ isql -v database1

and you should see

	+---------------------------------------+
	| Connected!                            |
	|                                       |
	| sql-statement                         |
	| help [tablename]                      |
	| quit                                  |
	|                                       |
	+---------------------------------------+
	SQL>
	
Ok, ODBC is working and set up.

## Compile and install RODBC

***Warning**: If you install RODBC the usual way, i.e. `packages.install("RODBC")`, you will get a version compiled with the non-working iODBC libraries. If you have already done this, `remove.packages("RODBC")` in R to get rid of it.*

The goal here is to link RODBC with the installed unixODBC library to make it work.

Download the source code of RODBC from [CRAN RODBC][rodbcdl] and choose the [package source][rodbcsrc] link (refers to the 1.3-8 version).

To compile and install it properly, first do:

	$ DYLD_LIBRARY_PATH=/usr/local/lib

This tells the compiler to use the unixODBC ODBC libraries installed by Homebrew in `/usr/local/lib` and not the iODBC ones installed by Apple in `/usr/lib`.

Then manually compile and install RODBC (you need the full path to the downloaded file for it to work):

	$ R CMD INSTALL /Users/Hiltmon/Downloads/RODBC_1.3-8.tar.gz

After a pile of configure and compile messages, you should see:

	** R
	** inst
	** preparing package for lazy loading
	** help
	*** installing help indices
	** building package indices
	** installing vignettes
	   'RODBC.Rnw'
	** testing if installed package can be loaded
	* DONE (RODBC)

## Test

All the installer does is test that the library loads. To see if it actually works, launch [RStudio][rstudio] and type:

	library("RODBC")
	odbcDataSources()

The response should be:
	   database1 	"PostgreSQL"

If you get an error message that contains `[iODBC]` in it, or a message that says `named character(0)`, it means you are using the wrong library version (the default and not the newly compiled one). Remove RODBC and start again.

Let me know if this works for you too.

Off to write some database queries now.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[rproj]:	http://www.r-project.org
[postgres]:	http://www.postgresql.org
[odbcadmin]:	http://support.apple.com/kb/DL895
[iodbc]:	http://www.iodbc.org
[unixodbc]:	http://www.unixodbc.org
[xcode]:	https://developer.apple.com/xcode/
[pgodbc]:	http://www.postgresql.org/ftp/odbc/versions/msi/
[rodbcdl]:	http://cran.r-project.org/web/packages/RODBC/index.html
[rodbcsrc]:	http://cran.r-project.org/src/contrib/RODBC_1.3-8.tar.gz
[rstudio]:	http://www.rstudio.com
[brew]:	http://brew.sh

