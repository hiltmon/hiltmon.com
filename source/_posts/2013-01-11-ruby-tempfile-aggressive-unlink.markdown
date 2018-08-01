---
layout: post
title: "Ruby Tempfile Aggressive Unlink"
date: 2013-01-11 10:49
comments: true
categories: [Ruby on Rails]
---

I often use Ruby’s `Tempfile` class when generating files in Rails for download. But something went wrong in the Rails 3.2.11 update.

Here is the code I normally use (as per the [Tempfile documentation](http://www.ruby-doc.org/stdlib-1.9.3/libdoc/tempfile/rdoc/Tempfile.html)):

``` ruby
...
begin 
  temp = Tempfile.new(“temp-file-name.xlsx”) 
  report = ReportClass.new(temp.path, params)
  report.generate
  send_file temp.path, :filename => “#{user_file_name}.xlsx", :type => "application/xlsx"
ensure
  temp.close
  temp.unlink
end
...
```

In short, create a temp file, stream the data to it in the report class, then send the file to the user. Ensure the file is closed and deleted after. Prior to Rails 3.2.11, this worked fine.

The problem after the 3.2.11 update is that the `temp.unlink` was happening *before* the file got sent (or maybe while it was being sent), leading to blank or corrupted files.

It turns out, the `temp.unlink` is not necessary any more. As long as you close a Tempfile using `temp.close`, Ruby’s Garbage Collector will delete the file for you, *once it no longer needs it*. Which means that the `send_file` will have a file available to send. I monitored my temp folder and it does indeed do this. 

So, remove the `temp.unlink` line in Rails 3.2.11 projects, and ignore the documentation. You can now generate and send files from Rails again.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*