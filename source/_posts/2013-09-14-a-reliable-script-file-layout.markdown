---
layout: post
title: "A Reliable Script File Layout"
date: 2013-09-14 14:44
comments: true
categories: 
---

I write a surfeit[^1] of Ruby scripts that I use every day at work, everything from sending, transforming and retrieving files to monitoring systems to glueing platforms together. Keeping these under control, forgettable[^2] and maintainable is very important to me. So over the past few years, I have migrated to a file layout and programming pattern that enables me to spin these up quickly, forget about them and yet get back and maintain them when things change.

In this post, I'll share this format and the thinking behind it as well as a few Ruby tricks that I rely on. <span class="light">And yes, it works just as well for Python or whatever other language you prefer to use.</span>

## The Script File Layout

### Traditional no layout version

Most people write scripts the old-fashioned *linear* way. For example, a script to get a file from an FTP server and upload it into a database would look something like this <span class="light">(not real code)</span>:

``` ruby Linear Example
#!/usr/bin/env ruby
	
require 'net/ftp'
require 'pg' # PostgreSQL Database
	
conn = PG.connect(dbname: 'd1')
	
Net::FTP.open('source.com') do |ftp|
	ftp.login('hiltmon', 'itsasecret')
	ftp.chdir('pub/data')
	ftp.gettextfile('the_data.csv')
end
	
CSV.foreach("the_data.csv") do |row|
	conn.exec("INSERT INTO t1 (c1, c2) VALUES ('#{row[0]}', '#{row[1]}';")
end
```

In short, connect to the database, get the file, parse the file and brute force insert it into the database. Simple, linear and it works!

The output is ... there is none.

**There is nothing *wrong* with this.**  Unless you have an excessive number of these to support and maintain. And you can *remember* the file format (what does `row[0]` and `row[1]` contain?) and *know* the assumptions implicit in this script (the retrieved file is saved in the same folder as the script) and know if it ran or not (there is no visible output or logging).

### Layout Version

Instead, I *over-engineer* all of these scripts and lay the code out logically. It requires more lines of code, but when things change, I find them a lot easier to find, read and maintain.

In short, all my Ruby scripts have the following common traits:

* They are created as classes where the class name is the Camel Case version of the file name (the Rails standard). That way the logic can be reused elsewhere. `get_data_file.rb` becomes `GetDataFile`.
* All constants appear at the top of the file where it's easy to find and change them.
* All classes have a `run` method that contains the main loop and each step is a function call, even if it is a single line step.
* All assumptions are documented in the file, but I prefer to make them explicit (for example, declaring where a file is saved).
* Called functions are always higher up in the file that the caller (the old C model still works) so navigating is easier.
* All classes are liberally festooned with `puts` statements which can be redirected to a log or be used when testing or manually running to see what is happening.

So lets look at the same above script using my standard format:

``` ruby Standard Model
#!/usr/bin/env ruby
	
require 'net/ftp'
require 'pg' # PostgreSQL Database

class GetDataFile
  
  SOURCE_URL = 'source.com'
  SOURCE_PATH = 'pub/data'
  FTP_USER = 'hilton'
  FTP_PASSWORD = 'itsasecret'
  FILE_NAME = 'the_data.txt'
  DEST_PATH = '/tmp/'
  
  DATABASE = 'd1'

  def initialize
    @conn = PG.connect(dbname: DATABASE)
  end
  
  # File name is overwritten every day
  def get_file
    puts "  GetFile #{FILE_NAME}..."
    dest_file_path = "#{DEST_PATH}#{FILE_NAME}"
    Net::FTP.open(SOURCE_URL) do |ftp|
    	ftp.login(FTP_USER, FTP_PASSWORD)
    	ftp.chdir(SOURCE_PATH)
    	ftp.gettextfile(FILE_NAME, dest_file_path)
    end
    puts "  File Saved to #{dest_file_path}..."
    dest_file_path
  end
  
  # 2010-01-01,99.0
  # 2010-01-02,99.17
  # 2010-01-03,99.51
  # 2010-01-04,98.73
  # 2010-01-05,99.23
  # 
  # File contains 2 columns, price date and the price
  # There is no header
  def save_file_database(file_path)
    puts "  Loading into Database..."
    count = 0
    CSV.foreach(file_path) do |row|
    	@conn.exec("INSERT INTO t1 (c1, c2) VALUES ('#{row[0]}', '#{row[1]}';")
      count += 1
      if count % 1000 == 0
        print "  Loading #{count} rows...\r"
        STDOUT.flush
      end
    end
    puts "  Loaded #{count} rows..."
  end
  
  def run
    puts "GetDataFile Starting..."
    file_path = get_file
    save_file_database file_path
    puts "GetDataFile Done..."
  end
  
end

app = GetDataFile.new
app.run()
```

That's a lot more code, 66 lines vs 16, but it is so much more readable and maintainable.

The output is more explicit too:

``` text
GetDataFile Starting...
  GetFile the_data.txt...
  File Saved to /tmp/the_data.txt...
  Loading into Database...
  Loaded 5016 rows...
GetDataFile Done...
```

Lets look at the key features:

* The constants are explicit and at the top. If the password changes, for example, it is easy to find (even easier with OS X Spotlight).
* The script is a class, with explicit methods for each step, making it easier to find which step has failed and fix that.
* Each step prints out when it starts, keeps you posted on that is happening and when it is finished. Debugging is built right in.
* The output also explicitly states where things are so you can find them, for example, where the file is saved.
* The order of the steps is explicit in the `run` function.
* A sample of the data being processed is placed in the comment above where it is used so I do not need to open the file to see what is there. I know what to expect.
* The code at the very bottom creates the class and kicks it off.

This may seem like overkill for such a simple 2 step script, but when you get to 5 or 10 step scripts, and a profusion of them, this pattern starts to make a lot more sense. As does the ability to add or remove steps as needed.

## File Naming Conventions

{% blockquote Phil Karlton %}
There are only two hard things in Computer Science: cache invalidation and naming things.
{% endblockquote %}

When you have only a few scripts, naming is quite easy. When you have a plenitude of them, not so much.

I follow the following approach for script names wherever possible: 

**keyword - source - data - transform - action - destination**

Where

* **keyword**: What is the script doing?
* **source**: From where does it get its data
* **data**: What is it working on?
* **transform**: If it does any additional work, what is it?
* **action**: What does it do with the data?
* **destination**: Where does it put it?

For example:

* **load_yahoo_prices_into_d1**: Loads data from yahoo that happens to be prices into database 1.
* **start_risk_server**: Kicks off a risk server daemon.
* **run_calculate_profit_and_loss**: A script to perform a single task.
* **load_city_temperatures_as_celcius_into_d1**: A load script with a transform.
* **send_d1_prices_to_freddy**: A script to get prices from database d1 and sends them to whomever freddy is.

The keywords I use to indicate behavior include:

* **start...** implies kicking off a daemon
* **kill...** implies terminating a daemon
* **run...** implies a task that starts and finishes
* **load...** implies an import of data
* **send...** implies delivery of data

With this pattern, I do not have to remember what a script is called, I can guess its name based on what I expect it should do. Also, the name of the script tells us all what it does.

## Tips and Tricks

Some tips and tricks I use a lot in these scripts:

* **Starting and Done**: The use of `starting` in a print statement indicates that a step is commencing. I often precede that with the function name to make it easy to see where the process is or where it failed. I use the `done` word to indicate successful completion.
* **Indentation**: I indent step messages by 2 spaces, and sub steps by an additional 2 spaces. This makes the depth of the message also explicit and yet I can see where a step starts and finishes, just like functions in code.
* **Color**: For more complex scripts, I also use terminal color output. Warnings are in yellow, errors in red, info in white and success in green.
* **Displaying Progress**: Look at the `print` statement followed by the `STDOUT` statement above. For long running steps, it's really nice to see progress, but it sucks if that progress causes the terminal to scroll. The Ruby `print` statement presents the text to the console without a new line (`puts` does that). Since there is no new line, terminal does not display the text yet. The `STDOUT.flush` command causes it to be shown. Note the `\r` at the end of the text string causes causes the terminal caret to return to the start of the line so the next print overwrites. So instead of seeing

	Processing 1000 rows...  
	Processing 2000 rows...  
	Processing 3000 rows...  
	Processing 4000 rows...  
	
	you get the same line being overwritten instead:

	Processing 4000 rows...  
	
## Properly Named and Laid Out Scripts

There are a lot of reasons for writing scripts, but I feel there is no reason not to do them properly and in a maintainable way. It does not take more than a few moments more to name them properly, code the structure and self-document the script, which will save you hours later on when things change. *And they always do.*

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[^1]: excess, overfill, abundance, bellyful, bucketload, glut -- a lot!
[^2]: No matter how good or smart you are, there is no way you can keep all of the file names, functions and purposes in your head over the long haul. Especially as things change often. Knowing you can forget something yet find it again later is far more valuable.