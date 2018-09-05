---
title: Client Side Event Tracking - Single Page Applications
layout: page
---

# Client Side Event Tracking - Single Page Applications #

On an old-fashioned server-side rendered website, where each navigation the user performs reloads their webpage, our pixel setup code will run on the client's browser every time a page loads. If you take a good look at the code snippet, you'll see that it automatically sends the "PageView" event immediately after load. This will not work for you if your website is a Single Page Application, because navigation is handles internally by your site's JavaScript, and so there is no full page load on navigation. This is solved using automatic page view tagging.

## Automatic PageView Tagging ##

The pixel will automatically detect changes to the page's history state and report a PageView event. Notice that an event will not be fired if the page URL has not changed. This behavior is turned on be default, but can be turned off needed. We recommend leaving this behavior on, but if you need to turn it off simply change your setup snippet to look like this - 

```javascript
/// ...
// first part skipped for brevity
/// ...
mktag.setToken("<YOUR-PARTNER-TOKEN>");
mktag.setAuto(false);
mktag.event("PageView");
```

In case you need to turn off automatic PageView tagging only for a specific part of your site, or a specific user flow, you can call `setAuto(true)` at any time to turn it back on.

## Self Tagging of PageView Events ## 

If your site's operation requires turning off automatic PageView tagging, you'll need to report these events by yourself, in accordance with your site's internal navigation logic. This is very simple to do - simply call the `event` function in the same way it is done in the setup snippet - 

```javascript
// notice there is no need for a parameters object, as the PageView event does not have any parameters
mktag.event("PageView");  
```
If you are having any issues regarding this topic, or if you are unsure as to what is the right way to report PageViews for your site, simply contact your account manager and ask for technical assistance.