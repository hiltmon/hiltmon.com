---
layout: post
title: "Attractive Multi-Line SQL Statements in C++"
date: 2016-04-26 20:19:26 -0400
comments: true
categories: 
---

I often need to embed SQL statements in C++ code. Unfortunately, many of mine are long and complex. Even the simple ones are wide. This leads to the following ugly code:

	std::string s8("SELECT id FROM lst_quotes WHERE route_id = $1 AND lst_request_id = $2 AND quote_id = $3;");

... which means I need a massively wide screen to view it (and it violates my 80-column rule), its not formatted legibly and even with wrap, its hard to understand — and this is a simple example. Its a maintenance nightmare.

Going multi-line, which is how SQL is usually written, makes things worse:

{% codeblock %}
std::string s8(
  "SELECT id "
  "FROM lst_quotes "
  "WHERE route_id = $1 "
  "AND lst_request_id = $2 "
  "AND quote_id = $3; "
);
{% endcodeblock %}

C++ compilers helpfully merge the strings, but I need to put in the quotes around each line (and have a space at the end of each line before the closing quote).

Or this monstrosity:

{% codeblock %}
std::string s8("\
  SELECT id \
  FROM lst_quotes \
  WHERE route_id = $1 \
  AND lst_request_id = $2 \
  AND quote_id = $3; \
");
{% endcodeblock %}

... where the end of line slashes *still* need to be added or the compiler gets upset.

**Ugly. Hard to maintain. Hard to read. Impossible to copy and paste. Unmaintainable.**

I want to be able to paste in SQL. Just SQL. As Is. From my database query tool.

### The Solution

The solution is a simple C++ variadic macro placed at the top of the file:

	#define SQL(...) #__VA_ARGS__

When used, this macro concatenates all lines between the parentheses, gets rid of newlines and, as an additional bonus, converts multiple white spaces into single ones. So this code (note the sexy formatting and excellent use of white space):

{% codeblock %}
  std::string s8( SQL(
  
    SELECT id
    FROM lst_quotes
    WHERE route_id = $1
    AND lst_request_id = $2
    AND quote_id = $3;
    
  ));
{% endcodeblock %}

Looks and works great. I can format, make legible and paste SQL in as necessary — the way SQL was meant to be.

When compiled, the resulting string is:

	SELECT id FROM lst_quotes WHERE route_id = $1 AND lst_request_id = $2 AND quote_id = $3;
	
... which is the desired compact version to pass on to the server.

**Legible. Easy to maintain. Easy to read. Simple to copy and paste. Very maintainable.**

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter.*