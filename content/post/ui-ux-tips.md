---
title: "UI/UX Tips and Tricks"
date: 2021-03-14T20:36:32-07:00
hero: ../../images/road.jpg
draft: true
authors:
    - Alex Stouffer
---

Here's a compilation of tips that developers can use to improve their User Interface (UI) and User Experience (UX). While this is not a comprehensive design guide, it's a short personal collection of tips I've gathered that's geared towards how to implement HTML elements in modern Web Application Development. I've listed some other guides with a focus on design at the bottom if you're interested.

### Hyperlinks

- Avoid Using `target="_blank"` when linking to new tabs. It will create a new tab every time a user clicks that link. Instead point the [target attribute](https://stackoverflow.com/questions/40026947/open-new-tab-on-link-markdown) at any unique name like `target="home"`. It will only open one instance of that tab, and redirect users to that specific tab in their browser.

- An updated method of allowing users to download a file from your link is to use the download attribute rather than the target attribute. it's an option used to designate a new file name when the client downloads the file. For example: `<a href="path/to/file123xyz.pdf" download="signup_newsletter.pdf">Here's your free newsletter</a>`. This method is prefered by users outside of windows who may have useless blank tabs open in their browser that they'll have to close manually.

### Other Guides

[105 Ecommerce UX Tips: How to Seduce Visitors to Buy](https://www.ecommerceceo.com/ecommerce-user-experience/)


