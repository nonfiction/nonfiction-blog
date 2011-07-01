For the last 9 years, nonfiction has hosted almost [all](http://calgarystampede.com) [of](http://cs.calgarystampede.com) [the](http://corporate.calgarystampede.com) [websites](http://venues.calgarystampede.com) for the Calgary Stampede. 

One thing that's different about their website usage is this - their premier event is a 10 day rodeo that happens every July - and their website traffic mirrors this.

![Visits to the site over the year](/blog/images/2011/06/27/visits.gif "Visits to the site over the year.")

This has given us a great opportunity to experiment with how to handle the incredible load changes - from 1,000 visitors per day to *60,000* visitors per day. At the peak, those visitors will look at approximately *350,000 pages* each day which translates to more than *10 million hits* each day.

For the first few years, the visitors were nowhere near the level they are now, so we were able to handle the traffic using the dedicated servers at [Rackspace](http://www.rackspace.com/). That worked great for a while, but there were a few limitations near the end of this time:

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

![View of Cachefly's network.](/blog/images/2011/06/27/cachefly.gif "View of Cachefly's network.")

That helped a ton with making the site responsive, but there was still one major issue - we needed to speed up the HTML for the site - #2 in the list above.

During certain days of the event, there are so many people requesting pages, that the site is heavily loaded and could be slow. We needed a "content accelerator" to help to:

1. Serve web pages very quickly.
2. Refresh those pages as they change.
3. Protect the content management system from one of the most popular sites on the internet - at least for a few days.
  
After some research and testing, we started using [Varnish](https://www.varnish-cache.org/) and we fell in love with it. Varnish is an amazing piece of technology - it helps with what's called the ["thundering herd problem"](http://en.wikipedia.org/wiki/Thundering_herd_problem) and it can make almost any website very fast in a short period of time.

We used this combination of Varnish and the Cachefly CDN last year (along with efficent programming techniques) - and it was a resounding success. We are able to handle a lot of website visitors with this combination - with a lot of capacity to grow if needed.

This year, we have a number of Varnish servers in a ring around the main websites, with the content distribution taking up the front line all around the world - and we anticipate being able to handle even larger traffic volumes without any issues.

Delivering web operations at this large scale for our clients is lots of fun for [nonfiction](http://nonfiction.ca/) - it continually presents us with unique challenges. In order to provide high quality service, our team keeps our [hosting technology](http://www.rackspace.com/cloud/cloud_hosting_products/servers/) [automated](http://gigaom.com/cloud/opscode-gets-chef-cooking-for-the-enterprise/), up-to-date and lean. We leverage powerful open source technologies first, whenever we can. We are not opposed to using paid software and for services either (such as Cachefly) yet we remain neutral to any software vendor. We’ve been doing this way for over 10 years and it works. 

We are seeing the overall trend of hosting towards this way of doing things. What kind of challenges do your sites face? Is your site fast, and its hosting automated, and up-to-date? We may be able to [help you](http://nonfiction.ca/contact.html).