---
layout: post
title: Hosting websites for the Calgary Stampede
author: Darron Froese
author-image: darron.jpg
author-link: http://twitter.com/darron
---

For the last 9 years, nonfiction has hosted almost [all](http://calgarystampede.com) [of](http://cs.calgarystampede.com) [the](http://corporate.calgarystampede.com) [websites](http://venues.calgarystampede.com) for the Calgary Stampede. We've designed a lot of them and are proud to use our content management system so they're mostly self-sufficient with updates and modifications.

One thing that's different about their website usage is this - their premier event is a 10 day rodeo that happens every July - and their website traffic mirrors this.

![Visits to the site over the year](/blog-beta/images/2011/06/27/visits.gif "Visits to the site over the year.")

This has given us a great opportunity to experiment with how to handle the incredible load changes - from 1,000 visitors per day to 60,000 visitors per day.

For the first few years, the visitors were nowhere near the level they are now - so we were able to handle the traffic using the dedicated servers at [Rackspace](http://www.rackspace.com/). That worked great for the first few years, but there were a few limitations near the end of this time:

  1. There were a few days where changes to the site needed to be avoided. Changes could introduce some major performance issues if they happened at peak times.
  2. Big crushes of traffic had the potential to do just that - crush the server.
  3. There wasn't a lot of room for error and we didn't like that.
  
So we started looking at options to:

  1. Make sure our other clients weren't affected.
  2. Keep the sites responsive so the Calgary Stampede visitors weren't impacted negatively.
  3. Allow us to keep the flexibility we enjoyed with respect to making changes during the event.
  
Some of the first items we had done and continued looking at were:

  1. Making sure the content management system was as efficient as possible. That involved tuning the database, the commands used to build pages, etc., etc.
  2. Making sure the images on the website are compressed down to the proper sizes.
  3. Making sure we were as efficient as possible when programming the site using HTML and CSS.
  
But that still wasn't enough - so we started looking at ["content distribution networks"](http://en.wikipedia.org/wiki/Content_delivery_network) or CDN's. You can think of a CDN as a bunch of computers placed all around the world - they are closer to a website's visitors so they're able to deliver certain parts of the website very quickly.

It works like this when you visit a website:

  1. You type in "www.google.com" to your web browser.
  2. You computer requests that page from the web server - and the web server delivers it.
  3. Then all of the images and related linked items are downloaded - 2 at a time.
  
It's during step #3 that the CDN can help tremendously - they place copies of your website content around the world, and your information doesn't have to travel as far.

We finally settled on [Cachefly](http://www.cachefly.com/) to help us serve the Calgary Stampede's sites. They have servers all around the world - and they serve all of the "dumb" content for the site - quickly and easily.

![View of Cachefly's network.](/blog-beta/images/2011/06/27/cachefly.gif "View of Cachefly's network.")

That helped a ton with making the site responsive, but there was still one major issue - we needed to speed up the HTML for the site - #2 in the list above.

During certain days of the event, there are so many people requesting pages, that the site is heavily loaded and could be slow. We needed a "content accelerator" to help to:

  1. Serve web pages very quickly.
  2. Refresh those pages as they change.
  3. Protect the content management system from one of the most popular sites on the internet - at least for a few days.
  
After some research and testing, we started using [Varnish](https://www.varnish-cache.org/) and we fell in love with it. Varnish is an amazing piece of technology - it helps with what we call the ["thundering herd problem"](http://en.wikipedia.org/wiki/Thundering_herd_problem) and it can make almost any website very fast in a short period of time.