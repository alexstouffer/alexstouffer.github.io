---
title: "Sean's Custom Art Shop"
date: 2021-09-15T19:14:07-08:00
hero: ../../images/seanform.JPG
draft: false
authors:
    - Alex Stouffer
---
Are you an artist looking to start your own online business? If you currently only have social media channels to show your work, this [Art Shop Solution](https://seanobrien.art) features a method to automate the sales process, and grouping your work by a product or service category. This project was developed to meet 3 main requirements: a blog, a shop, and no monthly fees. The 'nice-to-have' features of this project are currently in development, but we've delivered with those requirements a business solution built entirely on the JAMstack concept. For more details on how this project was built, please refer to [my retrospective on the project]({{< ref "/post/artretro" >}}).

#### Key Benefits
1. No direct sales calls necessary. Clients alternatively market their services via content creation, social influence, and inbound links to their products/services. 
2. Customers using the shop get a low-friction buying experience with transparent pricing information. This makes new customer acquisition easier.
3. Fast load times and low risk of server downtime from using Github as a Content Delivery Network (CDN).

This project is specifically developed to be hosted for free on Github Pages as opposed to other popular options like Netlify and AWS. While these are cost effective options for startups it did not meet our client's 3rd requirement (no monthly fees). As if free hosting weren't enough, Github generously includes the option of an SSL certificate for no cost. The integrated APIs only charge per transaction, so no minimum monthly costs are needed to maintain operation. The cost of an .art domain is only $4 for the first year. Overall you save $300 annually when compared to Shopify, Squarespace, WIX, and the cost to rent a hosted server. It's also a quick project to replicate in its current configuration allowing you to startup your business fast.

#### API Integrations
- [CommerceLayer](https://commercelayer.io/) - handles shopping cart functionality, customer information, inventory, SKUS & price lists.
- [Braintree Payments](https://www.braintreepayments.com/) - handles electronic ACH payments from the customer to the client.
- [Uploadcare](https://uploadcare.com/) - uploads photographs to the uploadcare server with an associated order ID.
- [Google Analytics](https://analytics.google.com/analytics/web/) (pending) - allows the client to monitor inbound traffic from various marketing methods.
- [Forestry.io](https://forestry.io/) (pending) - this particular client is savvy enough to use github for his updates, but this CMS integration is planned for future ease-of-use.

