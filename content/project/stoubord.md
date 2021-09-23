---
title: "Stoubord's Picks: Video RSS Directory"
date: 2021-04-08T19:14:07-08:00
hero: ../../images/StockProgramming.jpg
draft: false
authors:
    - Alex Stouffer
---

## Overview

Stoubord's picks is my first attempt to aggregate video content from YouTube creators by RSS feeds. The plan was to build this [project on wordpress](http://picks.stoubord.com) and then use the BuddyPress plugin to create a user-community. Users would update a directory of creators as well as niche tags on creator profiles to help the community find similar content.

### Core Functions

The whole project revolves our `Feeds` class found within our child theme's functions.php file. Within the Feeds class are three main functions: `fetch_directory_feed`, `data_render`, and `url_import`.



Those assist in pulling a single creator's RSS feed. Then outside of that class I've created a function called `fetch_all_directory_feeds` to run the fetch process for all creators listed when the homepage URL is triggered with the query parameter `?=fetch` attached.

```
// Fetch Directory Feeds
if (isset($_GET['fetch'])) {
    $fetch = $_GET['fetch'];
    if ($fetch === 'true'){
        echo '<script>console.log("fetch called successfully");</script>';
        fetch_all_directory_feeds();
    } else {
        echo '<script>console.log("no respect");</script>';
    }
}
```

### Fetching Feeds With Cron

This build at the moment utilizes the [wp_cron()](https://developer.wordpress.org/reference/functions/wp_cron/) function built into WP Core. This function will only run when a visitor lands on the page, and then only if our creator's latest 7 videos are new content that need to be posted to our server. In a project that I'd intend to run as a service, I would use a 3rd party cron service instead so that all creator video metadata is held as a record on the server from the point that the creator is added to the directory. In doing this users can come find information about content that may have been banned or otherwise censored.

### Issues

I had completed an MVP instance of the project suitable for one user. Once I moved onto the community feature, things seemed to get boxed in. Threads through BuddyPress' forum would often result in plugin developers telling users that features were in development and that they would update users at a later time. I also tried reaching out to other freelancing wordpress developers to pay for their consultation. Unfortunately I wasn't able to find the needed expertise. Considering that I would have to invest time learning about the buddypress plugin and how to customize its implementation on top of the wordpress framework, it seemed like a better use of time to remove multiple framework layers if possible, and re-build the project in react or vue.js where there's large sets of documentation and developers who might be better suited to help a solo developer. Wordpress could still be incorporated as a headless CMS if needed.