---
title: 'Keeping Secrets In Modular Development'
date: 2021-03-16T00:38:50-07:00
hero: ../../images/btc-franklin.jpg
draft: true
authors:
  - Alex Stouffer
---

API credentials are similar to passwords in that they help a server authenticate a user making a request for data. So how do you keep valuable data like a password secret when you're deploying a static site to a CDN with no backend?

### APIs Targeted by Bad Actors When:

1. Keys are a paid subscription
2. Keys & codebase allow users to do a variety of API calls

### Services

- [Fauna DB](https://fauna.com/jamstack)
- [CommerceLayer](https://commercelayer.io/)
- [UploadCare File Uploader](https://uploadcare.com/discover/uploadcare/)

### Notes

- [What is an API?](https://stackoverflow.com/questions/1453073/what-is-an-api-key#:~:text=An%20API%20key%20simply%20identifies,to%20all%20of%20your%20data.)
- [Why do APIs Require a Key & Secret?](https://stackoverflow.com/questions/1482472/when-working-with-most-apis-why-do-they-require-two-types-of-authentication-na/1501112#1501112)
- [How to Secure API Routes for JAMStack sites](https://stepzen.com/blog/how-to-secure-api-routes-for-jamstack-sites)
