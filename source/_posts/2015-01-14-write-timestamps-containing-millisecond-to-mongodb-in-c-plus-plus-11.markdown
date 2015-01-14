---
layout: post
title: "Write Timestamps containing Milliseconds to MongoDB in C++11"
date: 2015-01-14 18:42:40 -0500
comments: true
categories: C++
---

<span class="light">It took me several hours today to figure this one out, so I thought I'd write it up lest I forget.</span>

I have a C++11 application that rapidly writes new documents to a [MongoDB](http://www.mongodb.org) instance and I need high-resolution timestamps to determine the order things were written.

The problem is that the C++ standard `time_t` structure reports in seconds, so


	builder.appendTimeT("updated_at",
	    std::chrono::system_clock::to_time_t(std::chrono::system_clock::now())
	);


creates an ISODate *without* milliseconds in MongoDB.

There are many solutions to be found using `Boost::time`[^1], but since my code needs to be dependency-free and pure, I needed a C++11 clean solution.

MongoDB helps with its own `Date_t` class which is really just a `long long` number of milliseconds since the UNIX Epoch. So if I can generate that, we'd we dancing.

The solution in my `utilities` namespace, `DateTime` class is:


    namespace utilities {
  
      struct DateTime {
  
        ...

        static int64_t millisSinceEpoch()
        {
          std::chrono::system_clock::duration duration{
            std::chrono::system_clock::now().time_since_epoch()
          };
          return std::chrono::duration_cast<std::chrono::milliseconds>(duration).count();
        }
    
        ...
      }
    }  


This function constructs a C++11 `duration` object containing the number we need in an internal format, and then converts it to `milliseconds` for use.

The MongoDB c++ code also changes to:

    builder.appendDate("updated_at", utilities::DateTime::millisSinceEpoch());

And now we have [MongoDB](http://www.mongodb.org) ISODates with milliseconds that work perfectly.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*

[^1]: Yes, I know MongoDB uses Boost, but all I do is link to MongoDB's precompiled library, so my app remains *plausibly* independent. And I do not need to deal with matching MongoDB's boost version with my own.