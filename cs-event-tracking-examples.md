---
title: Client Side Event Tracking - Examples
layout: page
---

# Client Side Event Tracking - Examples #

### Search ###

When a user performs a search on your website, report what was his search query. You can also include the product ids for the first page of search results:

```javascript
mktag.event("Search", {
    search_term: "polka dot cushion pillow",
    product_ids: [
        "27316715",
        "20954807",
        "15857397",
        //...
    ]
});
```

### ProductView ###

Report this event when the user views a details page for a specific product:

```javascript
mktag.event("ProductView", {
    name: "Q62 Bluetooth Earphone",
    value: 22.5,
    currency: "USD",
    product_ids: [
        "zCymrMPAXUWd" //will usually contain only one ID
    ]
});
```

### CompleteRegistration ###

Report this event after a use completed their registration to the site. If the registration was paid, include the value and currency:

```javascript
//a paid registration
mktag.event("CompleteRegistration", {
    value: 9.99,
    currency: "USD",
});

//or a free one
mktag.event("CompleteRegistration");
```

### AddToCart ###

Indicate that a user added a product to his shopping cart, ideally including details about the item added:

```javascript
mktag.event("AddToCart", {
    name: "Joby GorillaPod 500 Action Black / Charcoal",
    value: 23.95, //the unit price of the product
    currency: "USD",
    product_ids: [
        "JOYGORILLAPOD500A" //will usually contain only one ID
    ]
});
```

### InitiateCheckout & Purchase ###

Both events have the same structure, and as their names imply are used to report that the user has started and successfully completed checkout, respectively:

```javascript
//starting checkout
mktag.event("InitiateCheckout", {
    value: 36,
    currency: "USD",
    products: [
        {
            product_id: "JSEL99JD7G",
            category_name: "Electronics > Arcade Equipment",
            category_id: 3356,
            price: 15,
            quantity: 1
        },
        {
            product_id: "SQ41DMpIJ9",
            category_name: "Animals & Pet Supplies",
            category_id: 166,
            price: 10.5,
            quantity: 2
        }
    ],
    num_of_products: 2
});

//and, assuming it's completed successfully
mktag.event("Purchase", {
    value: 36,
    currency: "USD",
    order_id: "AjEFN2uCu2",
    products: [
        {
            product_id: "JSEL99JD7G",
            category_name: "Electronics > Arcade Equipment",
            category_id: 3356,
            price: 15,
            quantity: 1
        },
        {
            product_id: "SQ41DMpIJ9",
            category_name: "Apparel & Accessories",
            category_id: 166,
            price: 10.5,
            quantity: 2
        }
    ],
    num_of_products: 2
});
```
