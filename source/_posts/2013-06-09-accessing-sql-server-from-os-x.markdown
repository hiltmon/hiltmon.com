---
layout: post
title: "Accessing SQL Server from OS X"
date: 2013-06-09 10:56
comments: true
categories: [ Scripting, python, ruby, microsoft ]
---

Every once in a while I need to access a Microsoft SQL Server database from my Mac, usually to create a data migration script. In the past I used a [commercial ODBC driver](http://www.actualtech.com). But ODBC on OS X was deprecated ages ago.

In this post, I'll talk about my current stack for accessing SQL Server databases via Ruby and Python and how to set it up. <span class="light">Note that I do not use [homebrew](http://mxcl.github.io/homebrew/), so these are all native installs.</span>

You will need Xcode and the command line tools installed, *which of course you already have*.

## FreeTDS

[FreeTDS](http://www.freetds.org) is a set of libraries that one can use from UNIX based systems to natively talk to SQL Server. Download it from their [stable release](ftp://ftp.freetds.org/pub/freetds/stable/freetds-stable.tgz) link to your `Downloads` folder (current version 0.91 as of writing).

Then, to build and install it:

``` sh
$ tar zxvf freetds-stable.tar
$ cd freetds-0.91
$ ./configure --prefix=/usr/local
$ make
$ sudo make install
```

To have FreeTDS default to the newer protocols for newer SQL servers, edit `/usr/local/etc/freetds.conf` and set:


```
[global]
# TDS protocol version
tds version = 7.1 # or 8.0
```

This works with SQL Server 2000, 2005 and 2008.

## Ruby

You need the [tiny_tds](https://github.com/rails-sqlserver/tiny_tds) Ruby gem to access SQL Server via FreeTDS from Ruby. I had a lot of trouble getting this gem to build on OS X 10.8.4 with Ruby 1.9.3 under RVM until I figured out the parameters needed to make it work with my FreeTDS and Apple's `iconv` library. Use the following *rather long* command:

``` sh
$ gem install tiny_tds -- --with-iconv-include=/usr/include --with-iconv-lib=/usr/lib --with-freetds-include=/usr/local/include/freetds --with-freetds-lib=/usr/local/lib
```

This compiles the gem with Apple's `iconv` lib and the FreeTDS we just installed.

After that, accessing a SQL Server database is easy. Here's a script to dump a table or a query to a CSV file:

``` ruby
require 'rubygems'
require 'tiny_tds'
require 'csv'

def write_csv(table, result)
  CSV.open("#{table}.csv", "wb") do |csv|
    result.each do |row|
      csv << row.values
    end
  end
end

def dump_table(table)
  puts "dump_table: #{table}"
  result = @client.execute("SELECT * FROM #{table}")
  write_csv table, result
end

def dump_query(table, query)
  puts "dump_query: #{table}"
  result = @client.execute(query)
  write_csv table, result
end

@client = TinyTds::Client.new(:username => 'username', :password => 'password', :host => '192.168.x.x', :database => 'database _name')

dump_table('table_name')
dump_query('table_name', "select * from table_name where date >= '2013-01-01'")

@client.close()
```

## Python

For Python, I tried the [pymssql](http://code.google.com/p/pymssql/) language extension. Installing this was quite easy:

```
$ sudo easy_install pip
$ sudo pip install cython
$ sudo pip install pymssql
```

And in a simple script:

``` python
import pymssql
connection = pymssql.connect(host = r'192.168.x.y:1433', user = 'username', password = r'password', database = 'database_name')

cursor = connection.cursor()

cursor.execute('SELECT count(*) FROM table_name ')
for row in cursor:
    print row
```

**Note** the use of Python raw strings for the host and password.

## Bonus Round: `isql`

If you are old school like me and want access to SQL Server from the command line, you really need the old `isql` command line. FreeTDS does have a `tsql` command to test access from the command line, but it is not fully featured.

But `isql` is part of ODBC which is deprecated. Oh, well, time to install [unixODBC](http://www.unixodbc.org). It's an oldie, but a goodie. Download from this [link](ftp://ftp.unixodbc.org/pub/unixODBC/unixODBC-2.3.1.tar.gz) or the downloads page. Then:

``` sh
$ ./configure --prefix=/usr/local
$ make
$ sudo make install
```

You also need to recompile FreeTDS with support for `unixODBC`, so go back to your FreeTDS folder and:

``` sh
$ cd freetds-0.91
$ ./configure --prefix=/usr/local --with-tdsver=8.0 --with-unixodbc=/usr/local
$ make
$ sudo make install
```

Following the instructions at [http://www.unixodbc.org/doc/FreeTDS.html](http://www.unixodbc.org/doc/FreeTDS.html), you need to register FreeTDS and create your first data source. My files look like this:

{% codeblock odbcinst.ini %}
[FreeTDS]
Description=v0.63 with protocol v8.0
Driver=/usr/local/lib/libtdsodbc.so
UsageCount=1
{% endcodeblock %}

and

{% codeblock odbc.ini %}
[TEST]
Driver=FreeTDS
Description=Test Database
Trace=No
Address=192.168.x.y
Port=1433
Database=database_name
TDS_Version=7.1
{% endcodeblock %}

To see if this is working, use the `osql` tool:

```
$ osql -S TEST -U user_name -P password -I /usr/local/etc
```

You can then access this database using good old `isql`:

```
$ isql TEST user_name password
```

**Note** that you may need to put `"` characters around the password if there are special characters in it.

## Commentary

It's quite sad that the popular Open Source databases like MySQL, PostgreSQL and MongoDB all have wonderful, fast, easy to install, native libraries for OS X and Linux, but the big commercial databases like SQL Server and Oracle still require these unpleasant hacks, ancient deprecated libraries or worse, Java! 

A lot of companies are moving their servers off Microsoft Windows and on to Linux, but they still need access to legacy data, and these hacks are just not that elegant or robust enough for true production use. Until these companies can migrate their databases off Microsoft and Oracle, they are going to have to live in transition and hope these hacks hold.

I think it's in Microsoft and Oracle's interest to release public libraries to access their databases from anywhere, including other platforms, in order to stay relevant and in the game.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*