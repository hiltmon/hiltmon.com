---
layout: post
title: "New Google Analytics for Status Board Server Edition"
date: 2015-06-07 19:47:54 -0400
comments: true
categories: [ Status Board ]
---

Last week, Google finally deprecated their non-Oauth APIs, which means that the [Google Analytics for Status Board](https://hiltmon.com/blog/categories/status-board/) code I have been publishing stopped working. Fortunately for us, Github user [erebusnz](https://github.com/erebusnz/gapi-google-analytics-php-interface) updated the PHP API to work with OAuth2 and we can access Google again. I have included it in a new version of the Server Edition Package.

## Quick Install Instructions

1. Download the [statusboard.zip]({{ root_url }}/files/statusboard.zip) file.
2. Expand it in the root of your web server. It creates a `statusboard` folder.
3. **New:** Register your application with Google Developers Console and get your Service Account email and P12 certificate file.
4. **New:** Determine your profile ID (its the number after the 'p' in the URL generated for your analytics)
5. **New:**Replace the 3 instances of &lt;----&gt; in *each* PHP file with your service account, P12 file name and profile ID.
6. The URL to use in Status Board is `http://<your-domain>/statusboard/analytics_<file>.php`, replacing `<your-domain>` with your server domain name, and `<file>` with one of `views` (graph), `hourly` (graph) or `pages` (table).

You should get something like this <span class="light">(Yes, my follower count is still tiny. Yes, I live in New York, but I still use Celsius for weather. And awesome Inbox Zero!)</span>:

{% img /images/status-board-000.png 715 537 %}

## Details

There are four files in the archive:

* `analytics_views.php` to present a graph of Page views, Visitors and New Visits for the past week for a site.
* `analytics_hourly.php` to present the same data over the last 24 hours.
* `analytics_pages.php` to show the top pages today.
* `gapi.class.php` is required to access Google Analytics

### Registering your API Access

You need to create a new Project in the [Google Developers Console](https://console.developers.google.com/project) in order to permit your web application to access Google's data.

{% img /images/status-board-001.png 529 191 %}

1. Click **Create Project**
 
{% img /images/status-board-002.png 532 241 %}

2. Give the Project a Name, such as "My-GAPI-Project"
3. Wait while Google does its thing and moves you to the Project Dashboard
4. Click on "APIs & Auth"
5. Click "APIs" and search for "Analytics"
 
{% img /images/status-board-003.png 529 196 %} 

6. Click on "Analytics API" then click "Enable API"

{% img /images/status-board-004.png 505 195 %}  
 
7. Click on "Credentials" to create a service account
 
{% img /images/status-board-005.png 537 197 %}  

8. Click on "Create new Client ID"
9. Choose "Service account" and click "Create Client ID"
10. Wait for it...
11. Google will download a JSON file to you. So nice of them.
12. Click "OK, got it"

### Fill in the Details 

You will now create, copy and paste the three elements needed for the Analytics PHP files to access Googles Analytics API.

{% img /images/status-board-006.png 638 138 %}

1. Copy the "Email address" which ends with "@developer.gserviceaccount.com" and replace the "&lt;Email address @developer.gserviceaccount.com&gt;" in each analytics PHP file.
2. Click "Generate new P12 Key". Google will send you a ".p12" file.
3. Copy this file into the SAME folder as the analytics PHP files.
4. Replace the "&lt;P-File Name.p12&gt;" in each Analytics PHP file with the execat name of the P12 file (including extension, no path needed)
5. Go to [Google Analytics](http://www.google.com/analytics/) and bring up one of the reports for the site you want to track.
6. Copy and paste the URL into a text editor, we're going spelunking for the profile ID. E.g. httpz://www.google.com/analytics/web/?hl=en#realtime/rt-overview/a1234567w1234567p9999999/"
7. Your profile ID is the set of digits after the 'p' at the end of the URL (in this case a fake 9999999). Paste that into the "&lt;Use Yours&gt;" in each analytics PHP file.

The top of each file should look something like this (codes are fake):

```
define('ga_profile_id','9999999');

require 'gapi.class.php';

date_default_timezone_set('America/New_York');

$ga = new gapi('729847129341293-938825he75l8mdabcxsh72hdqkdmpfobq273@developer.gserviceaccount.com', 
  'My-GAPI-Project-384idsucy44f.p12');
```

### Accessing from Status Board

For the 'hourly' "and 'views' graphs, create a new Status Board chart panel and set the URL to "&lt;your domain&gt;/status_board/analytics_hourly.php" and "&lt;your domain&gt;/status_board/analytics_views.php" respectively. For the Top pages list, create a new Status Board table and set the URL to "&lt;your domain&gt;/status_board/analytics_pages.php".

Enjoy.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*