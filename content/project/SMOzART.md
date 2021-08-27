---
title: "Sean O'Brien Paintings & Illustrations"
date: 2021-04-15T19:14:07-08:00
hero: ../../images/seanobrienart.png
draft: false
authors:
    - Alex Stouffer
---
## Project Overview 

[This Project](https://seanobrien.art) showcases sample artwork for a sole proprietor interested in selling their custom-commissioned art services online. Sean's a friend of mine and he was interested in starting a new business painting pets and family portraits. What we agreed to build for him was an ecommerce solution built entirely on the JAMstack concept using Hugo SSG as a storefront, Vue.js as a checkout application, and a few APIs to manage the cart, payments, and file uploading functionality. Since the storefront and checkout application are both hosted on github pages there's no monthly overhead to maintain the site, and they both come with an SSL certificate at no additional cost. Sean paid $4 for his domain the first year, and that's his only payment outside of transaction related fees paid to Braintree and CommerceLayer. 

### Milestones

1. MVP: a user can view the site and provide contact information to the client via Square appointment booking.
2. E-Commerce: a user can submit a single photo and purchase multiple canvases of that photo. (current stage, finalizing)
3. Analytics: the client can track information about who is visiting his site.
4. Headless CMS (low-priority): client can update photos to show latest work and write promo content via a web portal.

### API Integrations

1. [CommerceLayer](https://commercelayer.io/) - handles shopping cart functionality, customer information, inventory, SKUS & price lists.
2. [Braintree Payments](https://www.braintreepayments.com/) - handles electronic ACH payments from the customer to the client.
3. [Uploadcare](https://uploadcare.com/) - uploads photographs to the uploadcare server with an associated order ID.
4. [Google Analytics](https://analytics.google.com/analytics/web/) (pending) - allows the client to monitor inbound traffic from various marketing methods.
5. [Forestry.io](https://forestry.io/) (pending) - this particular client is savvy enough to use github for his updates, but this CMS is planned for future ease of use.

