---
title: 'Migrating Custom Post Types From WordPress to Next.js using GraphQL and Vercel Hosting'
date: 2022-06-14T00:38:50-07:00
hero: ../../images/birds-migrate.jpg
draft: false
authors:
  - Alex Stouffer
---

I built an [RSS reader](https://picks.stoubord.com) that pulls content from my favorite YouTube creators, and gives it to me without any kind of algorithmic influence. It’s a current portfolio project built with WordPress that relies on ‘the core’ of conventional WordPress CMS development. While I’m proud of the work I did using Advanced Customer Fields and writing PHP scripts, the site still doesn’t have a very nice User Interface/Experience to present the data that’s being served. Let’s document the improvement and integrate Next.js as a frontend framework. We’ll by using the plugin **`WP GraphQL`** to GET the `youtube_posts` Custom Post Type(CPT) from our WordPress instance using the headless CMS method.

### Targeting the CPT with a Custom GraphQL Query

The query below will pull YouTube specific content using GraphQL Composer. It’s available in the WordPress plugin dashboard. Convert a query made with composer into a URL you make make a test request with in the browser.

URL with GraphQL query added at end:

```jsx
http://picks.stoubord.com/graphql/?query=query ytQuery {
  youtubePosts(first: 10) {
    edges {
      node {
        title
				link
        id
        date
        featuredImage {
          node {
            mediaItemUrl
          }
        }
      }
    }
  }
}
```

URL encoded for web request (replace whitespace with `%20`):

```jsx
http://picks.stoubord.com/graphql/?query=query%20ytQuery%20{%20youtubePosts(first:%2010)%20{%20edges%20{%20node%20{%20title%20link%20id%20date%20featuredImage%20{%20node%20{%20mediaItemUrl%20}%20}%20}%20}%20}%20}&operationName=ytQuery
```

### Replacing Standard Posts with a Custom Post Type Query

[Colby Fayok’s Repo](https://spacejelly.dev/posts/how-to-fetch-graphql-data-in-next-js-with-apollo-graphql/) had the simplest query using GraphQL, and it used similarly formatted data from the SpaceX API, so I decided to use it as a template for querying the CPT. Under the `getStaticProps` function we update our URL endpoint to [`http://picks.stoubord.com/graphql/`](http://picks.stoubord.com/graphql/). Placing a console log statement right after the query will help by dumping the `data` object as a response and refining the object request from there. The final console statement was: 

```jsx
console.log('1st Console Statement :', data.youtubePosts.edges[0].node);
```

This value is passed as our prop value because it’s as deep as we could go without iterating through an array of the posts. In order to get the values from posts we have to alter the original repo’s map statement to change `launches` into `posts` and pass the value `data.youtubePosts.edges[0].node`. Then in each post during the map function we change the properties to include our node object nested within the JSON response:

```jsx
<a
  key={post.node.id}
  href={post.node.link}
  className={styles.card}
>
  <div>
    <Image
      src={post.node.featuredImage.node.mediaItemUrl}
      alt="Landscape picture"
      width={500}
      height={500}
    />
  </div>

  <h3>{post.node.title}</h3>
  <p>
    <strong>Published:</strong>{' '}
    {new Date(
      post.node.date
    ).toLocaleDateString('en-US')}
  </p>
</a>
```

I made a slight modification to the style to allow 4 pieces of content per row, and set a minimum height to the card so that every post is uniform. With that we have functioning listing page that get’s our latest 16 posts. It will still link back to the WordPress front end a this point, because we don’t have our post route setup on the Next.js project just yet. 

### Deploying on Vercel

Logging into Vercel and selecting which repo you want to import from your GitHub is easy, we just have to resolve any errors that may be logged in their output window. I had to install typescript to resolve a peer dependency, and remove any single quote marks within the Home component that weren’t escaped characters. After that the deployment redeployed smoothly and any pushes made to my repo will automatically reflect on the live server using their Continuous Integration/Development pipeline. You can visit the deployment here: [https://next-you-tube-rss-reader-4f8qoi33r-alexstouffer.vercel.app/](https://next-you-tube-rss-reader-4f8qoi33r-alexstouffer.vercel.app/)

### ERRORS:

#### Invalid src prop on next/image, hostname not configured

```jsx
Invalid src prop ([http://0.gravatar.com/avatar/01f5f8e7a914bfe3ef40569448588651?s=96&d=mm&r=g](http://0.gravatar.com/avatar/01f5f8e7a914bfe3ef40569448588651?s=96&d=mm&r=g)) on next/image, hostname "[0.gravatar.com](http://0.gravatar.com/)" is not configured under images in your next.config.js
```

To recreate, go to the GitHub repo [`https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress`](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress) and click the deploy button. Follow through with authenticating your GitHub account, and create a repo under your authorization through Vercel. Add the following value as the environment variable for WORDPRESS_API_ENDPOINT: `baseurl.com/graphql` . 

### FIX:

```jsx
module.exports = {
  images: {
    domains: [
      process.env.WORDPRESS_API_URL.match(/(http(?:s)?:\/\/)(.*)/)[2], // Valid WP Image domain.
      'baseurl.com',
      '0.gravatar.com'
    ],
  },
};
```
Update the domain list to include "0.gravatar.com" as specified in the error message. If match throws an error remove line 4 and leave the URLs

### What’s Next?

While we now have a listing page with various content, we want users to be routed to individual pages on Next.js, as well as querying other custom post type data like our creator directory and custom taxonomy to tag creators with certain interests.

### References:

- [https://nextjs.org/docs/basic-features/pages](https://nextjs.org/docs/basic-features/pages)
- [https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress)
- [https://www.freecodecamp.org/news/how-to-fetch-graphql-data-in-next-js-with-apollo-graphql/](https://www.freecodecamp.org/news/how-to-fetch-graphql-data-in-next-js-with-apollo-graphql/)
- h[ttps://www.apollographql.com/blog/graphql/basics/making-graphql-requests-using-http-methods/](https://www.apollographql.com/blog/graphql/basics/making-graphql-requests-using-http-methods/)
- [https://www.section.io/engineering-education/create-a-headless-cms-website-using-wordpress-nextjs-and-graphql/](https://www.section.io/engineering-education/create-a-headless-cms-website-using-wordpress-nextjs-and-graphql/)