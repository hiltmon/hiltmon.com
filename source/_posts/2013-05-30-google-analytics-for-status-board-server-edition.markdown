---
layout: post
title: "Google Analytics for Status Board Server Edition"
date: 2013-05-30 16:59
comments: true
categories: [ Status Board ]
---

<span class="light">Google has finally deprecated their GAPI interface which this used to talk to Google Analytics, sorry folks, it will no longer work. See the [New Google Analytics for Status Board Server Edition]({{ root_url }}/blog/2015/06/07/new-google-analytics-for-status-board-server-edition/) for an updated version. </span>

Dropbox went down today, and I found out when my [Status Board](https://itunes.apple.com/us/app/status-board/id449955536?mt=8&uo=4&at=10l894) stopped updating. This spurred me on to migrate my [Google Analytics for Status Board]({{ root_url }}/blog/2013/04/10/google-analytics-for-status-board/) scripts from Ruby and Dropbox over to server based PHP. <span class="light">Huge thanks to [Carl Franzon](http://www.carlfranzon.com/2013/04/google-analytics-panel-for-status-board/) for the starter code.</span>

**Warning: This version of the scripts requires PHP v5.3. It also uses a hacked version of the Google GAPI library that runs against the Google v2.4 API. The current Google API is v3, but that requires complex OAuth2 access, which is a pain in the *gazoot* to implement. <span class="light">Expect Google to deprecate the old API, probably tomorrow and without notice.</span>**

## Quick Install Instructions

1. Download the [statusboard.zip]({{ root_url }}/files/statusboard.zip) file.
2. Expand it in the root of your web server. It creates a `statusboard` folder.
3. Edit each of the `analytics_*.php` files with your login and password.
4. The URL to use in Status Board is `http://<your-domain>/statusboard/analytics_<file>.php`, replacing `<your-domain>` with your server domain name, and `<file>` with one of `views` (graph), `hourly` (graph) or `pages` (table).

You should get something like this <span class="light">(Yes, my follower count is still tiny. Yes, I live in New York, but I still use Celsius for weather.)</span>:

{% img /images/status-board-ga-2.jpg 715 537 %}

## Details

There are four files in the archive:

* `analytics_views.php` to present a graph of Page views, Visitors and New Visits for the past week for a site.
* `analytics_hourly.php` to present the same data over the last 24 hours.
* `analytics_pages.php` to show the top pages today.
* `gapi.class.php` is required to access Google Analytics, but this one has been hacked to use the v2.4 API.

For each of the `analytics_*.php` pages, change the first few lines with your own information:

{% codeblock lang:php %}
define('ga_email','hiltmon@gmail.com');
define('ga_password','i_aint_sayin');
define('which_profile',0); // The first profile
define('days_to_report', 7); // No of days excluding today!
define('ga_title','Hiltmon.com Stats');
date_default_timezone_set('America/New_York');
{% endcodeblock %}

If you have more than one Google Analytics profile (i.e. more than one site), you may need to change the profile, with 0 being the first profile in your list. I also recommend setting the timezone to your server timezone so that you don't fill your web logs with PHP errors.

Why choose these technologies?

* I chose to use PHP, <span class="light">which I intensely despise</span>, because that's the language most likely to be enabled on your web host. As it is on mine.

* I used the GAPI library because it works *without* OAuth. <span class="light">For now.</span>

If you'd prefer a more modern and robust approach, stick to the previous Ruby and Dropbox workflow at [Google Analytics for Status Board]({{ root_url }}/blog/2013/04/10/google-analytics-for-status-board/).

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*