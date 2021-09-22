---
title: "Project Retrospective: Sean O'Brien Art"
date: 2021-08-07T19:14:07-08:00
hero: ../../images/seanobrienart.png
draft: false
authors:
    - Alex Stouffer
---

This has been by far my favorite project to work on in regards to using a technology stack, specifically the JAMStack. It was my first time building an application this way, but it's rewarding on multiple levels: I've helped a friend succeed as an entreprenuer, built a product almost any business can start with, and saw valuable opportunities to extend on it. 

This site in particular uses two hosted github page repos based on code published by CommerceLayer for use with their API. The Hugo repo acts as our storefront by adding their `clayer-shopping-cart` widget into a static website. The Vue.js repo on github pages is a modified version of commerceLayer's checkout application. The other two APIs used in this project are Braintree Payments (Private key authorization is patched via CommerceLayer) and Uploadcare File Uploader, and these tools combined allow a user case where a customer can upload a photo and pay for an invoice pointing to the uploaded image link for artist reference and a smooth buying experience.

### Confusion Surrounding Payment Gateway Descriptors

Order processing through the Vue Application triggered a 422 patch error through CommerceLayer's API that held up the project for a considerable amount of time. I enlisted another person to help me look through the code and trace where things were breaking but couldn't figure things out as described by the error message: 
```
Error 92206 Url must be 13 characters or shorter and can only contain letters, numbers and periods.
```
A search of the web pulled up a couple pages about paypal error messages and listed them out, but the best I could find from those resources were the error statement itself. The confusion was primarily caused by receiving an error code served by Braintree API that originated from a CommerceLayer API request. What ended up causing the error turned out to not be about a URL at all but rather a payment descriptor given while entering values into your organization's payment gateway settings at CommerceLayer.

![DescriptorInfo](/images/DescriptorInfo.JPG)

The gateway info above works. You'll notice that the descriptor url isn't actually a URL at all, but in our previous gateway I specified .art believing that this needed to be a URL. That pushed us to 14 characters, but I couldn't figure out why there would be a requirement to have a URL operationally limited to 9 characters (4 characters would be fixed for whatever TLD like `.com`). All it is really, is another type of description on a financial statement of where the money was spent. However that didn't seem to be the case at the time as the form also had a 22 character descriptor name specifically for that purpose. That took rigorous validation via regular expression, but the Payment Gateway URL descriptor field didn't limit the character count to 13. While it's always important to follow an error code's specific message, sometimes that error code poorly describes the problem as is the case here. 

### Storefront User Experience
As you may have guessed, seanobrien.art looks very similar to my portfolio site. Well, that's because it is. Sean actually came to me as a client because he liked the layout of my page and that I could spin the site up for him quickly. We agreed that version 1 of his site would be very simple with only a blog to show his work and a button to schedule a consultation with him through Square appointments scheduling. So I began with the same forestry.io theme, Novela, and our 2nd version of the site modified the products/single.html template as the client's main shopping page. 

In this case we have single product (a portrait) with several pricing options (canvas size/color choice), and I needed to be able to use this information to get SKU IDs from our API. I decided to name the SKUs by two digits `00` representing width, a lowercase `x`, another two digits representing height, followed by a two letter suffix to represent Black and White `BW` or Full Color `FC`. The 8 by 10 inch canvas in black and white is therefore represented by the SKU `08x10BW`. Once we had our sku value selected I made sure that my form listeners checked whether all necessary values are true before setting the data attribute on the anchor tag prior to adding an item to the cart. Button elements could not be used on this page as it broke a Commercelayer script I couldn't edit.

Similarly I pulled the file URL and filename values from the Uploadcare file uploader upon submission to pass those values to the appropriate shopping cart data attributes. This helped propagate the client's photos on our checkout side of the application where the clients pay. That's when we have to then retrieve the order that we just pushed from our storefront.

### Checkout Processing Modification
The checkout side of things was developed originally for use on Netflify, but I wanted to stay on Github to avoid any monthly costs per the client's requirement. Initially the project would not run after cloning, because an Order ID needs to be attached to the base URL in order to query the API for that specific invoice. The original path to the checkout was `baseURL/orderID`, but Github requires that you point to an HTML file to serve a page and there's no named file in our directory that would match a revolving ID. The implemented solution was to change the orderID to be assigned to query parameters at the end of our URL like this: `baseURL?=orderID`. At that point the Vue project could pull the order and retrieve it on the live site. With our order processing issue resolved, orders began to process smoothly in the sandbox environment. All that's left is replacing the sandbox credentials to go live.

#### Upcoming Project Milestones
3. Google Analytics: the client can track information about who is visiting his site, and use the data for various marketing purposes.
4. Headless CMS (low-priority): the client can update photos to show latest work and write promo content via a web portal.
5. Host the site via FileCoin to adopt a decentralized approach. It's also supposedly cheaper than AWS.
