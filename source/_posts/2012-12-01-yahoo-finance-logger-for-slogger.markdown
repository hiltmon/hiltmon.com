---
layout: post
title: "Yahoo Finance Logger for Slogger"
date: 2012-12-01 16:24
comments: true
categories: [ Slogger ]
---

One thing I find myself doing every once in a while is trying to find out the [$AAPL](http://www.google.com/finance?q=NASDAQ:AAPL) share price for a given date. This usually requires a trip to Google Finance or Yahoo Finance and a need to download a data table to find what I need.

Wouldn’t it be nice if this information was in my journal?

So I spun up a simple [Slogger](http://ttscoff.github.com/Slogger/) plugin to do it. This plugin:

* Takes Yahoo data as at the time it runs (so theoretically you could run it multiple times a day). It does nothing on weekends, but it will run on holidays.
* Allows you to choose a list of tickers to report on.
* You can choose a detailed log or a simple one.

Given that it uses the Yahoo real-time API, it cannot be used to back fill data.

**Warning: This plugin is alpha code, so assume the usual no warranty legaleze, basically proceed at your own peril.**

## Installing the Plugin

* Save [Gist 4185229](https://gist.github.com/4185229) as `plugins/yahoofinancelogger.rb` (or copy it from `plugins_disabled`)
* Run `./slogger -o Yahoo` to create the `slogger_config` entry
* Edit the tickers list in `slogger_config` for the ones you want.
* Choose whether you want `show_details` true or false

## The Result

Here’s what it looks like with and without details:

{% img /images/yahoo-finance-slogger.jpg 640 480 %}

## Some ticker ideas

Try

* `^GSPC` S&P 500
* `^IXIC` Nasdaq
* `^DJI` Dow Jones Industrials
* `AAPL` Apple Inc
* `AUDUSD=X` AUD/USD Exchange Rate
* `USDJPY=X` USD/JPY Rate
* `^TNX` 10-Year Bond

Enjoy.

*See also [Google Analytics Logger for Slogger](https://hiltmon.com/blog/2012/11/14/google-analytics-logger-for-slogger/). Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*


