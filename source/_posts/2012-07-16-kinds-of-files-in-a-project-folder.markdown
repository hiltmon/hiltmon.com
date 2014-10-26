---
layout: post
title: "Kinds of Files in a Project Folder"
date: 2012-07-16 12:47
comments: true
categories: [Productivity]
---

In preparation for a client call, I wrote a quick and dirty script to count the kinds of files in a project folder to show them what's involved. I wanted a nice presentation, and the files grouped into categories. I also added parameters to *exclude* certain folder patterns from the counter.

The command is 

``` sh
$ ~/Scripts/cfile.rb ~/Projects/Kifu/code/kifu log tmp doc versions
```

The output is

```
Project File Counter v0.1 ©hiltmon.com 2012 http://hiltmon.com

Project: kifu
-------------------------------------------------------
Text Files:
    Markdown              :      1
    Plain Text            :      1
-------------------------------------------------------
Code Files:
    CoffeeScript          :      7
    CSS                   :     10
    ERB                   :    251
    HTML                  :      3
    JavaScripts           :     10
    Ruby                  :    265
    SCSS                  :     10
-------------------------------------------------------
Data Files:
    XML                   :      1
-------------------------------------------------------
Image Files:
    GIF Images            :      2
    Icon Images           :      1
    PNG Images            :    168
-------------------------------------------------------
Configuration Files:
    Configuration         :      3
    Rackup                :      1
    YML                   :      4
-------------------------------------------------------
Other Files:
    Unknown Kind          :      6
    .eot files            :      2
    Locks                 :      1
    Rake                  :      8
    .rdb files            :      1
    Fonts                 :      4
-------------------------------------------------------
TOTAL                     :    760 Files
-------------------------------------------------------
```

It aint pretty, as it was written very quickly. The script in a [gist](https://gist.github.com/hiltmon/3123720) is:

``` ruby
#! /usr/bin/ruby

# cfile.rb
# Hilton Lipschitz
# Use and modify freely, attribution appreciated
#
# This script counts the number and kinds of files in a project. Any additional
# parameters are treated as exclude folder regexes
#
# Requirements:
# 
#
# Examples:
# cfile ~/Folder/DBFS
# cfile ~/Folder/DBFS libs # Will exclude any folders with /libs/
# ~/Scripts/cfile.rb ~/Projects/Kifu/code/kifu log tmp doc versions # To skip all unnecessary rails trees

require 'rubygems'
require 'fileutils'

# No need to report these individually, so merge the counts
@merge_keys = {
	".xcbkptlist" => ".xcodeproj",
	".xcscheme" => ".xcodeproj",
	".xcuserstate" => ".xcodeproj",
	".pbxproj" => ".xcodeproj",
	".xcworkspacedata" => ".xcodeproj",
	".xcsettings" => ".xcodeproj",
	".scssc" => ".scss",
	".fnt" => ".ttf",
	".woff" => ".ttf"
}

# Make nice names for these
@descriptive = {
	".xcodeproj" => "Xcode Project",
	".c" 		 => "C/Objective-C",
	".h" 		 => "C/C++ Headers",
	".m" 		 => "Objective-C",
	".pch" 		 => "Precompiled Headers",
	".plist" 	 => "Plists",
	".png" 		 => "PNG Images",
	".txt" 		 => "Plain Text",
	".strings" 	 => "Strings",
	".coffee"    => "CoffeeScript",
	".conf"      => "Configuration",
	".css"       => "CSS",
	".csv" 		 => "CSV",
	".erb"       => "ERB",
	".gif" 		 => "GIF Images",
	".god" 		 => "GOD Configs",
	".html" 	 => "HTML",
	".ico" 		 => "Icon Images",
	".js" 		 => "JavaScripts",
	".lock" 	 => "Locks",
	".log" 		 => "Logs",
	".markdown"  => "Markdown",
	".old" 		 => "OLD",
	".pdf" 		 => "PDFs",
	".rake" 	 => "Rake",
	".rb" 		 => "Ruby",
	".scss" 	 => "SCSS",
	".ttf"		 => "Fonts",
	".xml"		 => "XML",
	".yml"		 => "YML",
	".ru"		 => "Rackup",
	".xib"		 => "XIBs",
	".storyboard" => "StoryBoards",
}

# Group the ones we know
@categories = {
	"Code" => [".c", ".h", ".m", ".coffee", ".erb", ".js", ".rb", ".css", ".scss", ".pch", ".html", ".xib", ".storyboard"],
	"Image" => [".gif", ".ico", ".png", ".pdf"],
	"Configuration" => [".xcodeproj", ".plist", ".conf", ".yml", ".ru", "strings"],
	"Data" => [".xml", ".csv"],
	"Text" => [".txt", ".markdown"],
}

@excludes = []
@counter_hash = {}

# Increment the count
def increment_key(key, value = 1)
	if @counter_hash[key].nil?
		@counter_hash[key] = value
	else
		@counter_hash[key] = @counter_hash[key] + value
	end
end

# Analyze a file by extension
def analyze_file(source)
	extension = File.extname(source)
# 	return if extension.length == 0
	increment_key extension
end

def process_folder(source)

	@excludes.each do |pattern|
		return if source =~ Regexp.new(pattern)
	end

	source_dir = Dir.new(source)
	source_dir.entries.each do |source_file|
		# Skip dot files and hidden files
		next if source_file =~ /^\./
		full_path = File.expand_path(source_file, source_dir.path)
# 		puts full_path
		if File.directory?(full_path)
			process_folder full_path
		else
			analyze_file full_path
		end
	end
end

def merge_keys
	@merge_keys.keys.each do |key|
		unless @counter_hash[key].nil?
			increment_key @merge_keys[key], @counter_hash[key]
			@counter_hash.delete(key)
		end
	end
end

if ARGV.length == 0
  puts "USAGE: cfile ~/Folder/DBFS <excludes>"
  exit
end

source = ARGV[0]
if ARGV.length > 1
	@excludes = ARGV[1..(ARGV.length)]
# 	puts @excludes
end

unless File.directory?(source)
  puts "  ERROR: Parameter 1 must be a project folder..."
  exit
end

process_folder source

merge_keys

puts
puts "Project File Counter v0.1 ©hiltmon.com 2012 http://hiltmon.com"
puts
puts "Project: #{File.basename(source)}"

used_keys = []
counter = 0
@categories.keys.each do |category|
	array = @categories[category]
	header_printed = false
	@counter_hash.keys.sort.each do |key|
		next if array.index(key).nil?
		unless header_printed
			puts "-------------------------------------------------------"
			puts "#{category} Files:"
			header_printed = true
		end
		used_keys << key if used_keys.index(key).nil?
		descriptive = (@descriptive[key] || "#{key} files").ljust(22)
		puts "    #{descriptive}: #{@counter_hash[key].to_s.rjust(6)}"
		counter = counter + @counter_hash[key]
	end
end

header_printed = false
@counter_hash.keys.sort.each do |key|
	next unless used_keys.index(key).nil?
	unless header_printed
		puts "-------------------------------------------------------"
		puts "Other Files:"
		header_printed = true
	end
	descriptive = (@descriptive[key] || "#{key} files").ljust(22)
	descriptive = "Unknown Kind".ljust(22) if key.length == 0
	puts "    #{descriptive}: #{@counter_hash[key].to_s.rjust(6)}"
	counter = counter + @counter_hash[key]
end

puts "-------------------------------------------------------"
puts "TOTAL                     : #{counter.to_s.rjust(6)} Files"
puts "-------------------------------------------------------"
```
