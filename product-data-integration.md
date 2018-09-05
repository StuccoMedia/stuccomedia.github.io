---
title: Product Data Feed Integration
layout: page
---

# Product Data Feed Integration #

Your product data feed is a structured data file containing a list of all your active products. It's recommended that product feeds be updated on a regular basis, as this greatly improved traffic volume and quality. 

### Feed Structure ###
Currently our system only supports Google Shopping compatible product feeds. Submitted feeds must fully comply with the [product data specification](https://support.google.com/merchants/answer/7052112) set by google, including the use of the google shopping product taxonomy, which can be [found here](https://support.google.com/merchants/answer/6324436).

> We currently don't support uploading delta feeds - only full inventory feeds are supported.

### Feed Format ###
Both CSV and XML feeds are supported. Feeds can be uploaded either in plain-text or as GZIP compressed files.

### Feed Delivery Options ###

There are 2 main modes of feed delivery - 
1. __Push__ - Every time you build a fresh feed you upload it to our servers, either manually or automatically. The main benefit of this system is that you have the best control over feed updates, freeing you upload feeds based on any internal logic. You could for example have the feed be uploaded every time a major stock update occurs internally. To learn more about setting up _push_ feed delivery, read [Updating Product Data - Push flow]({{ site.baseurl }}{% link product-data-push.md %}).
2. __Pull__ - Based on a pre-defined schedule, our system will make a request to your server to download the most updated feed. This solution gives you less control, but may work well if you already have a system for building and serving product feeds, and would like to use it instead of developing a new one. To learn more about setting up a _pull_ schedule for feed delivery, read [Updating Product Data - Pull flow]({{ site.baseurl }}{% link product-data-pull.md %}).

> After you review the different feed delivery options and choose the right one for you, please contact your Stucco account manger to help set it up.