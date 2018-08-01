---
layout: post
title: "RVM in TextMate 2"
date: 2013-01-16 20:04
comments: true
categories: [ Text Editors, TextMate ]
---

I use Ruby Version Manager ([rvm](https://rvm.io)) to manage the interpreters and gemsets for all of my projects. But the default install of [TextMate 2](https://github.com/textmate/textmate) uses the *system* ruby interpreter for internal command execution as well as for external runs. Here is how to use your `rvm` environment for both.

***tl;dr**: Set the `TM_RUBY` variable in preferences or your `~/.tm_properties` file to the path returned by `which rvm-auto-ruby` and restart. That will set the internal runner. For external runs from within TextMate 2, also comment out the shebang in the script before pressing `⌘R` (or run from the terminal directly). [Sublime Text 2](http://www.sublimetext.com/2) users, check the end of this post for `⌘B` use.*

## Testing the Internal Command Version

Of course you knew that you can use TextMate 2 to execute arbitrary ruby code in your file. To test which version is being used, create a new Ruby file in TextMate 2 and type: `RUBY_VERSION #⇥` which expands to 

``` ruby
RUBY_VERSION # =>
```

Then press `⇧⌃⌘E` or choose `Execute and Update ‘# =>’ Markers` from the gear menu. TextMate will run all the text on all lines before the `# =>` marker and place the output to the right. I get the default installed version of ruby:

``` ruby
RUBY_VERSION # => "1.8.7"
```

But if I go to my terminal, I have

``` sh
Galileo:~ $ ruby -v
ruby 1.9.3p194 (2012-04-20 revision 35410) [x86_64-darwin12.0.0]
```

## Setting the Internal Command Version

As per the instructions at [rvm’s TextMate](https://rvm.io/integration/textmate/) page, you need to find the path to `rvm-auto-ruby`. In a terminal run:

``` sh
Galileo:~ $ which rvm-auto-ruby
/Users/Hiltmon/.rvm/bin/rvm-auto-ruby
```

Set the `TM_RUBY` variable to this path. You could either do this in **TextMate / Preferences** in the **Variables** tab as shown ...

{% img /images/textmate-ruby-variable.png 480 350 %}

... or in your `~/.tm_properties` file.

``` ruby .tm_properties
...
TM_RUBY = "/Users/Hiltmon/.rvm/bin/rvm-auto-ruby"
...
```

The restart TextMate 2 and run the internal command test again:

``` ruby
RUBY_VERSION # => "1.9.3"
```

It now matches my `rvm` version.

## Testing the External Ruby Run

Create a new ruby file in TextMate 2 as follows:

``` ruby
#!/usr/bin/env ruby -wKU

puts RUBY_VERSION
```

And hit `⌘R` to run it. You should see:

{% img /images/textmate-run-with.png 638 256 %}

It seems to be using the *system* ruby.

## Using the RVM Ruby

To make this script use the current `rvm` ruby installation, just comment out the *shebang* line. It seems that the default TextMate 2 external script wrapper launches a clean shell that uses the *shebang* to choose the execution environment, but if there is no *shebang*, TextMate 2 uses the right one. So:

```
# <— COMMENTED OUT #!/usr/bin/env ruby -wKU

puts RUBY_VERSION
```

Gives

{% img /images/textmate-run-without.png 638 256 %}

It is now using the correct `rvm` version.

Don’t forget to uncomment the *shebang* line when you are finished.

## For Sublime Text 2 Users

If you want Sublime Text 2’s runner `⌘B` to use `rvm`, you need to open `~/Library/Application\ Support/Sublime\ Text\ 2/Packages/Ruby/Ruby.sublime-build`and replace the contents with this using the path returned from `which rvm-auto-ruby`:

``` json
{
  "cmd": [ "/Users/hiltmon/.rvm/bin/rvm-auto-ruby", "$file" ],
  "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
  "selector": "source.ruby"
}
```

*Note* that this will probably get overwritten when the Ruby package gets updated. *Note* also that neither `$HOME` or `~` work here, you need the full path.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
