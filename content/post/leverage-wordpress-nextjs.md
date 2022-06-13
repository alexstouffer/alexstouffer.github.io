---
title: 'Why You Should Integrate WordPress with Next.js'
date: 2022-06-13T00:38:50-07:00
hero: ../../images/NextVsWordpress.jpg
draft: false
authors:
  - Alex Stouffer
---

WordPress Sites account for ~40% of all websites and ~60% of all sites that use a Content Management System. Despite the overwhelming adoption, WordPress has some significant disadvantages that could be overcome with Next.js: 

### Slow page speeds & Poor SEO ranking
Wordpress can be excellent when optimized by a skilled developer, and maybe that's your case. However for every 1 site that's optimized there are at least a dozen that aren't. The reason for this is that most developers sell themes based on how they look rather than how they perform on search engine rankings. Designers often do not place any emphasis on functionality, because it doesn't drive their sales. SEO functionality through WP also requires external plugins to measure performance and this cannot be done with standardized built-in features.

Next.js is a massive improvement on SEO rankings, even in comparison to React.js, because it will generate all pages for your website in advance making them easier for search crawlers to index your site and rank it respectively. It improves on the speed of your site because it removes layers of complexity that wordpress adds to its codebase for 'no-code' developers. Every line of code contributes to longer load times. 

### Heavily Plugin Dependent
If WordPress requires libraries of plugins, just how standardized is the building process anyway? I can personally attest that WordPress will have you hitting a brick wall if the plugin you rely on has poor documentation. For instance, BuddyPress is the go-to plugin if you want to build a user-community on WordPress. When I searched for a solution to configuration problems and adding onto the plugin's functionality it was nowhere to be found in forums or documentation. I attempted to pay multiple developers self-titled as WordPress experts, yet none of the five developers interviewed could provide any assistance with building on top of the BuddyPress plugin, even at hourly rates in excess of $100 an hour. That's bad news for aspiring entreprenuers looking to develop products in a timely manner.

Next.js will allow you to scrap all of the proprietary plugins for the front-end and use WordPress as a 'Headless CMS' meaning that only the Database content will be used. All front end functionality will be built with Javascript similar to React. This provides much wider, easier developer support.

### Potential for server downtime
Whoops, AWS is down again. Whoops, GoDaddy has technical problems. My site is down again.

Nobody wants to say this and nobody wants to deal with it especially. However you can't just adopt the mentality that "if it's not broke, don't fix it", because you're in a constant arms race to market yourself to your customers more effectively than the competition. That requires constant refinement in your digital presence, and the ability to make improvements with minimal obstacles.

Next.js solves the server downtime problem by generating all of the pages for your website in advance and provides stakeholders the option of serving them from one or more Content Developer Networks (CDN) instead. CDNs have minimal downtime compared to traditional servers and there's less configuration and infrastructure maintenance involved, which translates directly to lower costs. CDNs only serve static content though, so parts of your site may still break if they rely on getting a server response for something like a loan application. However that's a big difference between having part of your site break vs the whole site disappearing. I pay nothing to host this site on GitHub pages CDN, and it never goes down. The information is always availabe to customers, and for page operators like myself it's free peace-of-mind.

### References

- [WordPress 6.0 Released: 'Arturo'](https://wordpress.org/news/2022/05/arturo/)
- [Tested: Is WordPress Good For SEO In 2022?](https://www.seobility.net/en/blog/wordpress-seo/)
- [Wordpress Marketshare Info](https://www.envisagedigital.co.uk/wordpress-market-share/)
