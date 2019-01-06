---
title: Client Side Event Tracking
layout: page
---

# Client Side Event Tracking #

Client side event tracking provides an easy way for you to pass information of user actions to Stucco. This information is used to optimize the traffic we deliver to you, and so it's important to make sure the integration is done correctly. Don't worry - we provide you with an easy to use JavaScript reporting library, meaning the average integration is only a few lines of code. It's super simple, just follow this instructions along, and you'll be on your way in no time.

> If you face any technical difficulties don't hesitate to contact your Stucco account manager and ask for technical assistance. 

### Setup ###

On every page that events should be reported from, paste the following HTML/JavaScript code between the `<head>` and `</head>` tags:

```html
<script type="text/javascript">
    !function(s,t,u,c,c,o){if(s.mktag){return;}var a=["\x67\x63\x6c\x69\x64","\x6d\x73\x63\x6c\x6b\x69\x64"];
    var q=[];var c={q:q,event:function(e,n){q.push(["event", e, n])},setToken:function(e){s.mktag.partner_token=
    e},transform:function(d){d.visitor_id=s.mktag.mktag_visitor_id;if(window.mktag.mktag_visit_id_expires_at
    &&new Date()>new Date(window.mktag.mktag_visit_id_expires_at*1000)){window.mktag.mktag_visit_id='';}
    d.visit_id=s.mktag.mktag_visit_id;return d;},setAuto:function(m){s.mktag.auto=m}},sp=s.location
    .search.substring(1)===""?{}:JSON.parse('{"'+s.location.search.substring(1).replace(/&/g,'","').replace
    (/=/g,'":"')+'"}',function(e,n){return""===e?n:decodeURIComponent(n)}),p="",pn="";for(var i=0;i<a.length;i++)
    if(sp.hasOwnProperty(a[i])){p=sp[a[i]];pn=a[i];break}s.mktag=s.mktag||c;var d=t.createElement("script");
    d.async=!0,d.src=""===p?u:u+"?"+encodeURIComponent(pn)+"="+encodeURIComponent(p),t.head.appendChild(d);}
    (window,document,"https://r.stuccomedia.com/resource/mktag.js");

    mktag.setToken("<YOUR-PARTNER-TOKEN>");
    mktag.event("PageView");
</script>
```
> This default setup code fires the PageView event and should work for most sites. If your website is an _SPA_, please take a look at [this page]({{ site.baseurl }}{% link cs-event-tracking-spa.md %})

Whenever you need to report an event simply call:
```javascript
mktag.event("<EVENT_IDENTIFIER>", eventPropertiesObject);
```
> For more examples of event reporting, take a look at our [examples page]({{ site.baseurl }}{% link cs-event-tracking-examples.md %})

### Event types ###

Below is a list of the 6 available events:

| Name                 | Description                                                                        | Parameters                                 | Required Parameters                        |
|----------------------|------------------------------------------------------------------------------------|--------------------------------------------|--------------------------------------------|
| Search               | The user has performed an intentional search using the site's search functionality | search_term, product_ids                   | None                                       |
| ProductView          | The user has viewed a product page                                                 | name, value, currency, product_ids         | None                                       |
| CompleteRegistration | The user registered to the site                                                    | value, currency                            | None                                       |
| AddToCart            | The user has added a product to his shopping cart/basket                           | name, value, currency, product_ids         | None                                       |
| InitiateCheckout     | The user has stated a checkout flow                                                | value, currency, num_of_products, products | value, currency, num_of_products, products |
| Purchase             | The user has successfully completed a checkout flow                                | value, currency, num_of_products, products | value, currency, num_of_products, products |

> Apart from the required parameters described in the table, the `currency` parameter is required whenever the `value` parameter is used

### Parameters ###

Here is a description for all the recommended parameters to be passed with the events as described in the table above.

| Parameter Name | Parameter Description                                                                | Parameter Type   |
|----------------|--------------------------------------------------------------------------------------|------------------|
| search_term    | The user's search query                                                              | string           |
| product_ids    | An array containing the IDs of the products relevant to the event being reported     | array of strings |
| name           | The title of the product relevant to the event being reported                        | string           |
| value          | The value corresponding the event being reported                                     | decimal number   |
| currency       | A three letter code for the currency of the value reported in the event               | string           |
| order_id     | The ID of the order being checked out (helps us to remove duplicated "purchase" events)       | string           |
| num_of_items   | The number of items being checked out                                                | number           |
| products       | The details of the products being checked out                                        | array of objects |
| product_id     | The ID of the product being checked out (as part item in the "products" array)       | string           |
| category_name   | The category name of the product being checked out (as part item in the "products" array) | string           |
| category_id     | The category id of the product being checked out (as part item in the "products" array) | number           |
| quantity       | The quantity of the product being checked out (as part item in the "products" array) | number           |
| price          | The price of the product being checked out (as part item in the "products" array)    | decimal number   |

### What's next? ###

You can see examples of all of how all these events are used in our [examples page]({{ site.baseurl }}{% link cs-event-tracking-examples.md %})
