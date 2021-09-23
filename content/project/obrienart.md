---
title: "Sean's Custom Art Shop"
date: 2021-09-15T19:14:07-08:00
hero: ../../images/seanform.JPG
draft: false
authors:
    - Alex Stouffer
---
Many people dream of owning their own business but they are limited to a small yet engaged audience on social media. If that sounds like a problem you are dealing with, this [Art Shop Solution](https://seanobrien.art) finally allows you to own your own business from home and without too much investment capital. This package features an automated sales pipeline and grouped products or services. It met the original stakeholder's 3 main requirements: a blog to promote work, a shop to sell directly from home, and no monthly fees. The 'nice-to-have' features of this project are currently in development, but I've delivered a business solution built entirely on the JAMstack. For more details on that, please refer to [my retrospective on the project]({{< ref "/post/artretro" >}}).

#### Key Benefits
1. No direct sales calls necessary. Shop owners alternatively market their services via content creation, social influence, and inbound links to their products/services. 
2. Customers using the shop get a low-friction buying experience with transparent pricing information. This makes new customer acquisition easier.
3. Fast load times and low risk of server downtime from using Github as a Content Delivery Network (CDN).
4. In its current configuration it's also a simple project to spin up quickly for new clients.

This project is specifically developed to be hosted for free on Github Pages as opposed to other popular options like Netlify and AWS. While these are cost effective options for startups it did not meet our client's 3rd requirement (no monthly fees). As if free hosting weren't enough, Github generously includes the option of an SSL certificate for no cost. The integrated APIs only charge per transaction, so no minimum monthly costs are needed to maintain operation. The cost of an .art domain is only $4 for the first year. Overall these page operators save $300 annually when compared to Shopify, Squarespace, WIX, and the cost to rent a hosted server.

#### API Integrations
- [CommerceLayer](https://commercelayer.io/) - handles shopping cart functionality, customer information, inventory, SKUS & price lists.
- [Braintree Payments](https://www.braintreepayments.com/) - handles electronic ACH payments from the customer to the client.
- [Uploadcare](https://uploadcare.com/) - uploads photographs to the uploadcare server with an associated order ID.

