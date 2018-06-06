---
layout: post
title: "Reprogramming my Brace Style Mind"
date: 2013-01-07 13:24
comments: true
categories: [programming, c++]
---

Each and every programmer has their own style of coding, their own preferences for how code should look, and are generally happy to argue the case for their preference. Somehow these discussions became heated, and the most fights happen over **spaces vs tabs** (See [Tabs versus Spaces: An Eternal Holy War.](http://www.jwz.org/doc/tabs-vs-spaces.html) and [Death to the Space Infidels!](http://www.codinghorror.com/blog/2009/04/death-to-the-space-infidels.html)), **the 80 column rule** (See [In defense of the 80-column rule](http://zuzu-curl.blogspot.com/2010/02/in-defense-of-80-column-rule.html)) and **brace indent style**.

Recently, I have had to change my choices, they were wrong. But a bit of history first.

## The 1980’s/1990’s Compact Style

When I started programming, we use *tab* characters because it kept files smaller, limited code to *80-columns* because we had to print out code *a lot* on 80-column dot-matrix printers and we followed Kernighan and Ritchie’s *original* [C Programming Language](http://www.amazon.com/gp/product/0131103628/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&tag=hiltmon-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0131103628) book’s convention of braces on the same line. Code looked like this:

``` c
int main(int argc, char *argv[]) {
        int a = rand() % 100;
        if (a > 25) {
                call_a_function();
                call_another_function();
        } else {
                call_b_function();
        } // end if
} // end main
```

This style worked. Tabs in those days were always 8 stops wide, which meant that you could not indent much before slamming into the 80-column limit, forcing you create lots of smaller functions, a good thing. And braces on the same line meant more code would appear printed on each page.

But there were some bad things too. We started using shorter variable names to gain additional indent levels within files, making the code harder to read and maintain. We did not put any whitespace between lines of code to cram more on the printed page, making the start and end of blocks harder to find (and so we would comment block ends so we’d know what they were). And we lost a lot of limited coding space because the indents were so wide.

## 2000’s Expansive Style

In the 2000’s, we all seemed to switch to Microsoft’s C and C# conventions, namely 4 spaces instead of tabs, unlimited line length and all braces on their own lines, like so:

``` c#
int main(int argc, char *argv[])
{
    int a = rand() % 100;
	
    if (a > 25)
    {
        call_a_function();
        call_another_function();
    } 
    else
    {
        call_b_function();
    }
}
```

Spaces for indents meant we did not have to deal with different editors’ tab sizes (or their fickle users’ preferences). And since we had stopped printing code, we could focus on trying to make it more readable using white space, longer variable names and braces on blank lines to make our blocks stand out (so we could see the start and end of block by matching columns).

But that too led to problems. With unlimited line lengths (and larger screens), we no longer felt the need to limit the number of indents in a function and started to create larger monolithic functions. And since editors at that time did not wrap code very well, programmers would often find themselves unable to see the code on the left while horizontally scrolled and working on the end of a long line to the right. Code became harder to read, and side-by-side comparisons became impossible.

So in the early-2000’s, I chose my side in these arguments: I agreed with 4 spaces because it took editors out of the equation, kept the 80-column rule to force-limit indenting and changed to braces on their own lines to improve readability.

I stuck with it, argued it like all geeks do, and thought I’d never change.

## 2010’s Canonical Style

Until now. Or really until I started using Xcode 4’s intelligence and snippets.

You see, Xcode defaults to 4 space indents, so that stays the same. I think it handles limited line lengths rather well with intelligent wrapping, which means the scroll to the right issue and the 2-up issues are resolved. But it started to drive me nuts that it’s default brace style in snippets seemed *inconsistent*. Sometimes braces would be on the *same* line and sometimes on their *own*. What? No! I need consistency.

Take the default `initWithNibName` code snippet:

``` objective-c
- (id)initWithNibName:(NSString *)nibNameOrNil bundle:(NSBundle *)nibBundleOrNil
{
    self = [super initWithNibName:nibNameOrNil bundle:nibBundleOrNil];
    if (self) {
        self.title = NSLocalizedString(@"Detail", @"Detail");
    }
    return self;
}
```

*The function block braces are on their own line, ala 2000’s C#, but the `if` block braces are not, ala 1990’s C style.* Surely this is a royal screw-up! From Apple! The style gurus!

It turns out that no, it’s not a screwup, the hybrid brace style that they are using is the *original* Kernighan and Ritchie style which was *messed up in the early printings of the C book* to save space. The brace style rules, as per K&R are:

{% blockquote Wikipedia http://en.wikipedia.org/wiki/Indent_style#K.26R_style %}
When adhering to K&R, each function has its opening brace at the next line on the same indentation level as its header, the statements within the braces are indented, and the closing brace at the end is on the same indentation level as the header of the function at a line of its own. The blocks inside a function, however, have their opening braces at the same line as their respective control statements; closing braces remain in a line of their own, unless followed by an else or while keyword.
{% endblockquote %}

It turns out, that this *true* K&R style is the *canonical* form for braces for all C derivative languages, including C++, C# and Objective-C. That’s from the designers of the languages themselves.

Guess I’ve been doing it wrong and arguing it wrong all these years.

So I have changed my brace style mind. I am still a 4 space man. I still run a 80-column page guide, and try to keep within it, but now rely more on the editor to smart-wrap long lines. But I now adhere to the *true* K&R brace style:

``` c
int main(int argc, char *argv[]) 
{
    int a = rand() % 100;
		
    if (a > 25) {
        call_a_function();
        call_another_function();
    } else {
        call_b_function();
    }
}
```

I’m still getting used to it.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*