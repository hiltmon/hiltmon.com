---
layout: post
title: "Magical Migrations"
date: 2014-02-08 11:46:50 -0500
comments: true
categories: 
---

<span class="light">As I am writing this, I am using magical migrations to perform a full data transplant across three servers, each with 100+GB of data, with a single command. Yep, I'm chilling and writing a blog post while replacing the entire data scaffolding of my firm as if it were just another cold Saturday. Magical indeed.</span>

*TL;DR: [Rails migrations][RM] and [Capistrano][CAP] deploys create a stable, reliable, testable, reversible and no-fault way to manage and execute production database changes, no matter the platform size or complexity.*

When I started at the current firm, I knew I would be designing and developing a wholly new, proprietary platform. At the time, all I knew was that it would be big and complex and that I did not yet have a handle on what it would be.

But I did know these to be true (for that matter not-knowing that you do *not* know something is knowledge in itself):

* I did not know the complete requirements at the start, and most likely would not know the complete requirements in the middle.
* I would not get the database design and architecture right the first time, and probably not the second time either.
* Things will change. The business, requirements and architecture will change and continue to do so. Which means I needed to be flexible in choosing what to do and how to do things.
* I will have more than one database server, many in fact. Some as backups or read-slaves, some as replicas, some as islands, and some for testing and modeling.
* I need to be able to track, manage and automate the myriad of changes to all of these servers using tools because there is no way I could do it in my head.
* I would probably be the only person doing this for the first year or so.

In the past, the way I have done this was to create separate database projects for each database and then created SQL files to save the queries and data definition commands to change these databases. Then, in preparation for deploy, we'd backup the production databases to a staging area, then manually run the SQL to migrate the database and then run a test suite to see if we got it all. If it all worked, we'd then spend a weekend doing this on the production servers. More often than not, something had been forgotten, not placed in the database project, or not updated as things changed, and we'd leave production deploy alone until the staging model was rebuilt and tried again. 

And *that* was better than the older ad-hoc method of just having a dedicated Database Administrator patch the databases manually on deployment days (which is how it worked in the dark past and still does in a lot of firms).

I needed a way to automate all database changes, a way that was integrated in my development workflow and a way to deploy these changes with ease.

The solution: [Rails migrations][RM] and [Capistrano][CAP] deploys.

<span class="light">Aside: Fortunately I am using Rails for a few of the web servers on the platform which made choosing Rails migrations easy. But I am also running a bunch of [Sinatra][SIN] servers for web services, Python programs for analytics, C++ programs for high-speed work and looking at [Node.js](http://nodejs.org) and [GoLang](http://golang.org) for future projects that all access our databases. And who knows what else will access them in the future.</span>

For the main database, I created a single master [Ruby on Rails](https://rubyonrails.org/) project. I then share that model between all my Rails projects, see my [Rails Tricks - Sharing the Model](https://hiltmon.com/blog/2013/10/14/rails-tricks-sharing-the-model/). All other projects just assume the current schema. For other databases, more Rails projects, several of which have no web interface at all, or are in support of a non-Ruby project.

### Creating and Managing Database Schema Migrations

But lets focus on the main database.

In my environment, this runs on a pair of servers in a remote data center for production and on an additional database server used for analytics. Development is done locally, as is staging. All three of these main servers are accessible from the same code base, so they all need to have the exact same schema. And all have over 100GB of data in them which is *business critical* and so I cannot screw up deploys and changes.

**All database changes are in Rails migrations.**

**All of them.** No exceptions.

Create a new table, its a migration. Add a column, another migration. New index, another migration. Add seed data, a migration.

As a developer then, it's easy to use and test. Create and edit a migration (or Rails model for new tables) and `rake db:migrate` to apply the changes. Not perfect, `rake db:rollback`, correct the model or migration and `rake db:migrate` again. 

I never, ever use SQL directly on the database to make schema changes. It violates the protocol. All changes are in migrations, all of them.

A few Rails migration tips:

* Create all tables as Rails models which create migrations. It adds a bit of code to the project, but makes it easy to test the database or create web views of the data later. For example:

``` bash
$ rails generate model Table description:string price:decimal{12-2}
```

* **Do not be afraid to use raw SQL in migrations**. That which Rails migrations cannot do, can be done with SQL in migrations. I use it all the time to transform or backup data. For example:

``` ruby
...
# Fixup codes
execute "UPDATE securities SET coupon_type = 'FIX' WHERE coupon_type = 'LKD'"
execute "UPDATE securities SET coupon_type = 'FIX' WHERE coupon_type = 'ADJ'"
execute "UPDATE securities SET coupon_type = 'FIX' WHERE coupon_type = 'SPC'"
...
```

* **Make all `up` migrations reversible**. This is easy as Rails takes care of most of these as long as the migrations are non-destructive. For destructive migrations, such as when you are moving data to new tables or removing columns, I create temporary tables or dump files to save the data being deleted, and reverse these in the `down` part. Only when I am very sure that these changes are fixed and deployed to production do I create migrations to drop these temporary tables - these being the only non-reversible migrations I have. For example, in an `up` migration for a changing table, I first back it up:

``` ruby
def up
	execute %Q{
		CREATE TABLE ex_table (
			id     INTEGER     NOT NULL,
			column_1 character varying(255),
			...
		CONSTRAINT ex_table_pkey UNIQUE(id)
	);}
    
    execute %Q{
    	INSERT INTO ex_table (id, column_1, ...)
    	SELECT id, column_1, ...
		FROM table;
	}
    
	remove_column :table, :column_1
end
```

In some cases, I even dump data to files to enable reverses or just to have backup copies. For example, in a `down` (reverse) migration where I dropped a table in the `up`, I may have:

``` ruby
def up
	# Save the data for Justin Case :)
	execute "COPY (SELECT cusip, price_date, price, yield) FROM historical_prices) TO '/tmp/hp.csv' WITH CSV;"
	drop_table :historical_prices
end
	
def down
    create_table :historical_prices, { id: false } do |t|
		t.string :cusip, limit: 9
		t.date :price_date
		t.decimal :price, precision: 12, scale: 4
		t.decimal :yield, precision: 12, scale: 6
    end
    
    # Get it back
    execute "COPY historical_prices (cusip, price_date, price, yield) FROM '/tmp/hp.csv' WITH CSV;"
    
    add_index :historical_prices, :cusip
    add_index :historical_prices, :price_date
end
```

* One big negative of Rails migrations when creating tables is that they create an `id` field automatically. This is useful if running a Rails web app or using ActiveModel. But for tables that have no need of these, or are being accessed by applications that do not need `id` columns, here's how to get rid of it: Just add `{ id: false }` to the `create_table` line as in:

``` ruby
class CreateNoIDTable < ActiveRecord::Migration
	def change
		create_table :no_id_table, { id: false } do |t|
			t.string :my_key, limit: 9
			t.string :my_text

			t.timestamps
    	end
	end
end
```

You can also get rid of the Rails `created_at` and `updated_at` columns by commenting out the `t.timestamps` code.
	
* **Seed data in migrations**. Sometimes you need to put data into tables when creating them, for example when creating code to string reference tables. Put the data into the migration and have the migration load it. For example, using Rails model creates:

``` ruby
class CreatePurposeClasses < ActiveRecord::Migration
	def up
		create_table :purpose_classes do |t|
			t.string :class_code, limit: 4
			t.string :class_name, limit: 32

			t.timestamps
		end
		
		add_index :purpose_classes, :class_code, unique: true
    
		# Populate
		PurposeClass.create!(class_code: 'AUTH', class_name: 'Authority')
		PurposeClass.create!(class_code: 'BAN', class_name: 'Bond Anticipation Note')
		PurposeClass.create!(class_code: 'BLDG', class_name: 'Building ')
		...
```
	
### Deploying Database Schema Migrations

I have been using [Capistrano][CAP] for years to deploy Rails applications. And it works well. I use it now to deploy my main database Rails project that contains all the necessary migrations to all servers.

It takes just one command to send the code over and one more to make all the changes and I can be sure all my staging and production databases are perfect.

To deploy:

	$ cap production deploy
	
To migrate:

	$ cap production deploy:migrate
	
I prefer to do this in two steps in case the initial deploy fails, in which case Capistrano rolls it back safely without affecting the database. I do worry about Mr Murphy.

In order to choose *which* server and database to migrate, I use Capistrano's multistage extension. Each database gets a stage. For example, I have the following at the top of my main project's `config/deploy.rb` file:

``` ruby
# Enable multi-stage support
set :stages, %w(staging analytics production)
set :default_stage, "production"
require 'capistrano/ext/multistage'
```

I then have separate files in the `config/deploy/` folder for each server (stage) that sets the server names and roles. For example the `config/deploy/analytics.rb` file sets the `:db` role to the analytics database server, and the `config/deploy/production.rb` file sets `:db` to the production server.

I can then easily run:

	$ cap analytics deploy:migrate
	$ cap production deploy:migrate
	
I really rely on Capistrano's ability to rollback code deploy errors, and on Rails migrations ability to rollback database migration errors to prevent massive failure situations.

### The Benefits

I get a lot of benefits from using [Rails migrations][RM] and [Capistrano][CAP] deploys (Magic Migrations):

* Database management is part of my development process, not an add-on, separate process to be scheduled and managed.
* I do not need to 'remember' the state of databases.
* I do not need to document changes, I have a log of them in the migration files.
* I do not need to insert data into tables after migrations as the seed data is included. 
* One command to deploy and one to migrate. I get my weekends back.
* If anything goes wrong, it can be undone and rolled back as if nothing has happened.
* I just know that each database has the latest and correct schema for all my systems and can access them with confidence.

So here we are, I'm running one of these right now that is significantly changing the core architecture of my firm's platform and instead of manually doing the work, or staring helpless at the process, or even having to worry if it fails, I'm writing this post.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[RM]: https://guides.rubyonrails.org/migrations.html
[CAP]: http://capistranorb.com
[SIN]: http://www.sinatrarb.com