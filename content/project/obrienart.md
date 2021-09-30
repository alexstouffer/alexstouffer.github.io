---
title: "Sean's Custom Art Shop"
date: 2021-09-15T19:14:07-08:00
hero: ../../images/seanform.JPG
draft: false
authors:
    - Alex Stouffer
---
Many people dream of owning their own business but they are limited to a small yet engaged audience on social media. If that sounds like a problem you are dealing with this [Art Shop is the solution](https://seanobrien.art). You can finally own your own business from home and without too much investment capital. This package features an automated sales pipeline and grouped products or services. It met the original stakeholder's 3 main requirements: a blog to promote work, a shop to sell directly from home, and no monthly fees. The 'nice-to-have' features of this project are currently in development, but I've delivered the client a custom business solution built entirely on the JAMstack. For more details on that, please refer to [my retrospective on the project]({{< ref "/post/artretro" >}}).

#### Key Benefits
1. Sales calls are optional. Shop owners alternatively can market their services via content creation, social influence, and inbound links to their products/services. 
2. Customers using the shop get a low-friction buying experience with transparent pricing information. This makes new customer acquisition easier.
3. Fast load times and low risk of server downtime from using Github as a Content Delivery Network (CDN).
4. In its current configuration it's also a simple project to spin up quickly for new clients and extend from there.

This project is specifically developed to be hosted for free on Github Pages as opposed to other popular options like Netlify and AWS. While these are cost effective options for startups it did not meet our client's 3rd requirement (no monthly fees). As if free hosting weren't enough, Github generously includes the option of an SSL certificate for no additional cost. The integrated APIs only charge per transaction, so no minimum monthly costs are needed to maintain operation. The cost of an .art domain is only $4 for the first year. Overall these page operators save a couple hundred annually when compared to Shopify, Squarespace, WIX, or the cost to rent a hosted server.
#### Art Shop API Integrations
- [CommerceLayer](https://commercelayer.io/) - handles shopping cart functionality, customer information, inventory, SKUS & price lists.
- [Braintree Payments](https://www.braintreepayments.com/) - handles electronic ACH payments from the customer to the client.
- [Uploadcare](https://uploadcare.com/) - uploads photographs to the uploadcare server and pushes referal info (link, filename) to CommerceLayer.

While this exact project is an 'on-demand' type of service, it's also possible to clone one for an inventory of pre-made items. The portrait builder page allows users to select SKUs on the fly based on the portrait parameters, while typically only one product is offered on a page. As we move forward, we'll be integrating Google Analytics and tracking methods to drive traffic to the site and increase sales. I'll be sure to share more about that journey as it continues.



