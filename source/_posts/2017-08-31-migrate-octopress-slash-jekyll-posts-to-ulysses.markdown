---
layout: post
title: "Migrate Octopress / Jekyll Posts to Ulysses"
date: 2017-08-31 07:49:38 -0400
comments: true
categories: 
---

I wanted to move my published writing stashed in my Octopress/Jekyll site into my current writing workflow environment, [Ulysses](https://ulyssesapp.com). Dragging and dropping the files from the `_posts` folder was not an option, because:

- The file names were messy
- There is no title in the file, it's in the Markdown metadata
- I wanted to keep the publication date on the imported files

So, I wrote a *horrible* script to do it.

The script takes a `_posts` Octopress or Jekyll folder and processes each file into an `OUT_PATH` as a set of clean Markdown files, making a few changes along the way. It’s a mix of Ruby to handle the YAML front matter and shell commands to do the actual work. And it runs as follows:

- For each file in the `IN_PATH`
- Parse the YAML front matter to get the title and publish date
- Create a new file using the title and write a Markdown H1 to it
- Append the existing file data to the new file
- Depending on how the publish date is formatted (old was a string, new is a time), *touch* the new file to set the original publish date

After that, I just dragged and dropped the Markdown files into Ulysses which kept the formatting and dates.

The script itself is below. *Its terrible and you dare not use it.* But maybe it has some ideas to help you run your own conversion.

	#!/usr/bin/env ruby
	
	require 'rubygems'
	require 'yaml'
	require 'time'
	  
	# IN_PATH = "/Users/hiltmon/Projects/Personal/HiltmonDotCom/source/_posts/"
	# IN_PATH = "/Users/hiltmon/Projects/Personal/NoverseDotCom/code/noverse/source/_posts/"
	IN_PATH = "/Users/hiltmon/Downloads/_posts/"
	OUT_PATH = "/Users/hiltmon/Desktop/Blog/"
	
	Dir.new(IN_PATH).each do |path|
	  next if path =~ /^\./
	  
	  basename = File.basename(path)
	  puts "Processing #{basename}..."
	
	  posthead = YAML.load_file(IN_PATH + path)
	  title = posthead['title'].sub("'", '')
	  
	  # Create a new file and add the H1
	  cmd2 = "echo \"# #{posthead['title'].strip}\n\" > \"#{OUT_PATH + title}.md\""
	  %x{#{cmd2}}
	  
	  # Append the original Markdown
	  cmd1 = "cat #{IN_PATH + path} >> \"#{OUT_PATH + title}.md\""
	  %x{#{cmd1}}
	  
	  # Mess with the file time
	  if posthead['date'].is_a?(Time)
	    cmd3 = "touch -t #{posthead['date'].strftime("%Y%m%d%H%M")} \"#{OUT_PATH + title}.md\""
	    %x{#{cmd3}}
	  else
	    file_date = Time.parse(posthead['date'])
	  
	    cmd3 = "touch -t #{file_date.strftime("%Y%m%d%H%M")} \"#{OUT_PATH + title}.md\""
	    %x{#{cmd3}}
	  end
	end
	

The result:

{% img /images/blog-in-ulysses.jpg 550 278 %}

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*
