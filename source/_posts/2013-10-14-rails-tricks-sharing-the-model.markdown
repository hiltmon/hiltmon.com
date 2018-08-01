---
layout: post
title: "Rails Tricks - Sharing the Model"
date: 2013-10-14 13:58
comments: true
categories: [ Ruby on Rails ]
---

I am building a series of Rails applications for different users and use cases, but they all hang off the *same* database schema. Using canonical Rails, that means a single, massive rails app with a bunch of controllers, a heap of views and a complex security model.

I prefer small, focussed apps, so I decided to share the model instead. Here's how it works.

## Sharing the model

Lets call the the first rails project *Master*. Generate it as usual and create a few models and migrations to set up the database. In my case, the *Master* rails application is used to do nothing more than import, export and allow users to view the data in the model's database tables.

	rails new Master --database postgresql
	cd Master
	rails generate model model1 ...
	...
	rake db:create
	rake db:migrate

Lets now create a reporting app, called *Reporting* that will use the same model as *Master*.

	cd ..
	rails new Reporting --database postgresql
	cd Reporting
	
**Do not create any models or migrations in this project, you do them all in *Master*.**

To copy the models, create a new `rake` task in a new file in *Reporting* called `lib/tasks/sync.rake`:

``` ruby
namespace :sync do
  
  desc 'Copy common models and tests from Master'
  task :copy do
    source_path = '/Users/Hiltmon/Projects/Master'
    dest_path = '/Users/Hiltmon/Projects/Reporting'
        
    # Copy all models & tests
    %x{cp #{source_path}/app/models/*.rb #{dest_path}/app/models/}
    %x{cp #{source_path}/test/models/*_test.rb #{dest_path}/test/models/}

    # Fixtures
    %x{cp #{source_path}/test/fixtures/*.yml #{dest_path}/test/fixtures/}
    
    # Database YML
    %x{cp #{source_path}/config/database.yml #{dest_path}/config/database.yml}
  end
end
```

Change the `source_path` to point to the root of the *Master* project and the `dest_path` to point to the root of the *Reporting* project. The run it:

	rake sync:copy
	
The script copies the `app/models`, `test/models`, `test/fixtures` and `database.yml` files from *Master* to *Reporting*. As far as Rails is concerned, these were created via genuine rails commands and the Rails engine will make these models available in your reporting views and controllers. The `database.yml` file will also make Rails point to the same database as *Master*.

Two rules need to be followed to make this work:

1. All models or migrations are done in *Master* and only in *Master*. That includes any changes to model files.
2. Run a `rake sync:copy` every once in a while to bring the *Reporting* project up to date after changes in *Master*.

Top Tips:

* If you run `rake db:migrate` in the *Reporting* project, no harm will be done (because there are no migrations in it). But the `schema.rb` file will be regenerated. Which is cool.
* You can add additional projects that use the same shared model, I have 5 at the moment.

## Rejected Options

I could have just symlinked the model and db folders between the projects, and therefore not needed the `rake` task. But that only works for a single development system and single developer. I would have to relink for each new computer or developer that needs to work on these projects.

I also could have used `git` submodules to provide a common repository for the copied code, but that would mean that I could not use the regular `rails` and `rake` commands for models and migrations, which defeats the purpose of using Rails.

## Result

As a result of sharing (ok, copying) the models this way, I have several Rails applications running off different servers providing different services to different users all running off the same back-end database. Each application is smaller, simpler, easier to manage and easier to code and maintain. As long as discipline is maintained in that the models and migrations are only performed in the *Master* project, this trick works great.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*