---
layout: post
title: "More TextMate 2 Basics"
date: 2014-01-20 14:07:30 -0500
comments: true
categories: [Text Editors, TextMate]
---

{% img right /images/textmate.png 128 128 %}

Previously, I wrote about the [TextMate 2 Basics](https://hiltmon.com/blog/2013/11/09/textmate-2-basics/) that I use all the time, and I recommend you read [that](https://hiltmon.com/blog/2013/11/09/textmate-2-basics/) post first. This post follows up with a *mish-mash* of more tools, ideas and tricks that I also use surprisingly frequently.

## Text Tools

TextMate 2 tries to reduce the number of keystrokes you need to make to generate good code. There are many ways it does this but today I want to talk about *auto-pairs* and *completions*.

### Auto-pairing

Auto-pairing is when you type in a character that should be paired in code, and the editor ensures the paired character is also inserted. For example, pressing the `(` key inserts a `)` as well (and where the caret is between the paired characters). This works well for all brace keys (`[`, `(` and `{`) and quote (`'` and `"`) characters.

But TextMate takes it to the next level:

{% img right /images/tm-2-basics-2-1.png 140 210 %}

- **Wrap Selected**: Select some text and press the opening key in an auto-pair set. Instead of replacing the selection with the key pressed like other editors do, TextMate wraps that selection in the correct pair. 

  For example, to to correctly bracket an expression such as `a / b + c`, select the `b + c` bit using ⌥⌘← and hit `(` to get `a / (b + c)`.
  
{% img right /images/tm-2-basics-2-2.png 200 210 %}
  
- **String Interpolation**: In Ruby, you can interpolate a variable's value in a string using the `#{}` construct. TextMate is aware of the context and if you press the `#` key inside a string that can be interpolated, TextMate uses auto-pairing to wrap the selection in the interpolation braces.

  For example, to convert `user_name` in the following line `puts "Name: user_name"`, select `user_name` and press `#` to get `puts "Name: #{user_name}"`. 
  
  Note also that if the string does not support interpolation (a single quoted string), pressing `#` inserts a `#` character only. Smart.
  
Of course the big problem with auto-pairing is that in most other editors, you need to then navigate past the closing pair character to continue working. In TextMate, if you type the closing character manually, it knows, and just moves your caret along without duplicating the close. Or you can use `⌘↩` to go to a new line, leaving the closed pairs behind, or `⌘→` to navigate over all the closes.

### Tab and Esc Completions

TextMate has two kinds of completions, "tab" (⇥) completions and 
"esc" (⎋) completions.

{% img right /images/tm-2-basics-2-3.png 200 170 %}

**Tab completions** were invented in TextMate and have improved in TextMate 2. Tab completions operate by typing in a few letters and pressing the tab (⇥) key. TextMate attempts to match the characters before the cursor to the tab completions available for that language or context, and if a match is found, it puts the completion in. For example, in Ruby, typing `def⇥` will insert `def function_name\n\nend` and highlights `function_name` for you to overtype.

{% img right /images/tm-2-basics-2-4.png 360 231 %}

You can find the currently available tab completions in the cog menu at the bottom for each language. The best way to learn them is to see what is available and then start using them. For example, in Ruby, I always use `cla⇥` to create Ruby classes, `mod⇥` to create Ruby modules and `ea⇥` for quick `each` loops. I strongly recommend you check out and learn the tab completions for our favorite languages in TextMate. You will save a ton of keystrokes.

Note that TextMate is aware at all times on the language context you are in. Which means that different language completions are available in different parts of a code file. For example, in a Rails `.erb` file, HTML completions are available unless you are inside a `<% ... %>` construct, in which case, Ruby tab completions work.

{% img right /images/tm-2-basics-2-5.png 200 230 %}

**Esc completion** saves you keystrokes within a code file by completing *function* and *variable* names that exist in the *current* file. <span class="light">To get project level completions, you need to look at `ctags` which I intend to cover in a future post.</span>

Start typing a function or variable name that already exists and press the esc (⎋) key to see the first recommended match. Press ⎋ again to find another match or cycle through the choices.

**Just remember, in completions, tab (⇥) is for code, esc (⎋) is for names.**

## The File Browser

The File Browser has changed completely in TextMate 2 and it took me a while to get used to it. This is because the *new* file browser is more like a Finder window than the old project file manager.

To switch between the editor and the File Browser without using the mouse, hit `⌃⌘⇥` (Control-Command-Tab). You can then use the arrow keys to navigate the tree. Use `⌘↓` to open the selected file (just like Finder). When in the editor, to reveal the current file in the file browser, hit `⌃⌘r` ("Reveal").

{% pullquote %}
If you mouse instead (like I do), {" single-click the file icon to open it in the editor. "} Single-clicking the name just selects it (just like Finder). Double-clicking the file name opens the file too. *Once you get used to single-clicking the icon, opening files becomes so much easier.*
{% endpullquote %}

## Editor Tabs

The tabs at the top are also smart in TextMate 2. If you have the file browser open and request a file that is in the same tree as the currently open folder, it opens in a new tab. If not, it opens in a new window. TextMate therefore tabs or windows depending on the context of the file, automatically determining project membership. This even works when you use `mate <filename>` from the command-line.

We all open a lot of tabs as we work, especially in Rails development. And it's a pain to close each tab individually. If you `⌥-click` on a tab close button, all other *saved* tabs will close.

You can also drag a tab out of the tab bar (or double-click on it) to move it to a new window. If you want it back, use the **Window / Merge All Windows** menu. Currently this merges all windows into one, here's hoping they use the smart logic for creating tabs and windows to find a way to merge to project-based windows someday.

## Fonts and Themes

{% img /images/tm-2-basics-2-6.jpg 700 245 %}

Since we all have different tastes and preferences, TextMate comes with a lovely set of built-in themes which are fully customizable. You can change the theme from the **View / Theme** menu. 

To install  a new theme, download a `.tmTheme` file and double-click it. Then look for the new theme on the **View / Theme** menu. I use my own [CombinedCasts.tmTheme](https://hiltmon.com/files/CombinedCasts.tmTheme) theme (See [Multiple Themes in TextMate 2 - The Hiltmon](https://hiltmon.com/blog/2013/02/22/multiple-themes-in-textmate-2/)) but there are hundreds out there to choose from.

{% img right /images/tm-2-basics-2-7.jpg 300 189 %}

In my case, I have set TextMate to be the default editor for all my script file formats, from `.sh` to `.rb` and `.py`. I also use QuickLook a lot to browse code files before opening them. If TextMate is the default for a file, it's QuickLook generator is used and it now renders code files using your selected theme. A nice touch.

One recent change in TextMate 2 has been the way it accesses and uses fonts. I highly recommend using the **View / Fonts / Show Fonts** menu at least once after changing a theme to select the font and size that you prefer. Some old themes use incorrect names for fonts and the new model guesses incorrectly. If you have a global `.tm_properties` file and set your font there, make sure the name is the correct there too.

## Script Writing Tips

If you use TextMate to write Shell, Ruby or Python scripts, use the environment string (or "shebang" `#!`) to make things easier to run:

{% img right /images/tm-2-basics-2-8.png 200 210 %}

- Start each file with the right environment string. This helps the shell know what runtime to use to execute the file. Type `env⇥` at the top of the file and TextMate will insert the correct environment "shebang" into the file. **It will also mark the file as executable on first save.** So instead of running `ruby my_script.rb`, you can just type `my_script.rb` on the command line to run it.
- Speaking of the command line, hitting `⌃⇧O` (the letter O) will open a fresh terminal session in the current folder of the file.  But if you prefer the TextMate output window, `⌘r` in TextMate will launch the environment specified in the file's "shebang" and display the output in the output window.

## Quick Keyboard Tips

Three additional keyboard tricks I use a lot:

- `⌃"`: Toggles between single-quotes (`''`), double quotes(`""`) and quoted strings (`%Q{}`). I use this a lot in Ruby as I normally create strings without interpolation (single-quotes) and then need to change it later. It works on the quotes surrounding the cursor.
- `⌃_`: Toggles the selected name between CamelCase (`HomeBrew`), underscores (`home_brew`) and nerdCase (`homeBrew`), useful when you use the wrong convention in code (especially if you code in multiple languages).
- `⌃⌥⌘V`: Brings up TextMate's clipboard history. Now you can copy, copy, copy, then switch files and paste, paste, paste.

## Some Useful Bundle Tips

### Source Code Control

If you use git, mercurial or subversion, install the matching bundle. You then get the following benefits:

- TextMate shows the current status of each file in the file browser. You can see which files have uncommitted changes instantly.
- The `⌘y` key brings up a menu of Source Code Control commands that you can use instead of leaving the editor and using the command-line. Options include seeing the changes to be committed, amending commits, viewing branches and of course, the ability to commit changes. The git bundle even has a config option to enable you to change your global settings.

### The TODO Bundle

{% img right /images/tm-2-basics-2-9.png 300 152 %}

I don't know about you, but I often leave `TODO` and `HACK` comments in my code to remind me about things, *and then forget about them*. The TODO bundle in TextMate 2 searches the current project tree for comments with `TODO`, `FIXME`, `CHANGED` and `RADAR` and displays them in the output window. Just hit `⌃⇧T`. You'll never forget again.

{% img right /images/tm-2-basics-2-A.png 300 173 %}

To add your own markers, go to the cog menu, find the TODO bundle and click **Preferences...**. Add a new marker and replace the regular expression to catch the rest of the comment. Hit `Done`, restart TextMate and run TODO again to see your new marker matches.

### SQL Bundle

I only found this one recently, but it comes in handy a lot. I write a lot of code that queries PostgreSQL databases, which means I write a lot of SQL. Many of the processes and views I write contain embedded SQL statements.

Before finding this bundle, I used to have to copy the SQL from TextMate into NaviCat, test and run it, then copy it back. And I could never be sure that I got it all until I ran the program.

{% img right /images/tm-2-basics-2-B.png 300 194 %}

The SQL bundle supports MySQL and PostgreSQL only, but it works rather well. Start by setting up your connections in **Cog Menu / SQL / Preferences...**. Then, to test a SQL statement, just select it in TextMate and hit `⌃⇧Q`. If TextMate picks the wrong database, open **Cog Menu / SQL / Preferences...** and highlight the correct database then click `Done`. `⌃⇧Q` will run the SQL against the correct database now.

{% img right /images/tm-2-basics-2-C.png 300 152 %}

The output window is also a Database Browser, so you can use it to browse databases, their tables and see what their fields are named while coding.

The SQL bundle is pretty basic, but for quick and dirty views and tests it works great.

## Fin

So those are some more TextMate 2 features that I use all the time. Hopefully you found a few more gems in there that could help you out.

If you missed the first post, check out [TextMate 2 Basics](https://hiltmon.com/blog/2013/11/09/textmate-2-basics/).

*If you have any awesome TextMate 2 features or keys you cannot live without, please share them in the comments.*

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*