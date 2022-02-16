---
title: "NFT Sales Tracker"
date: 2022-01-21
hero: ../../images/Gemma2.jpg
draft: false
authors:
    - Alex Stouffer
---
## Project Overview

I built a [Nifty Bot](https://github.com/alexstouffer/NFTBot) that tracks sales for a single collection of Non-Fungible Tokens (NFTs). For showcasing purposes I've chosen to spin up a bot for a new collection in the space that I love called "[GEMMA](https://twitter.com/Bot_Gemma_NFT)" by Los Angeles based artist Tristan Eaton. This collection is a series of 5k portraits all generated programatically under the artist's direction. I feel it's a great representation of what this new area of art has to offer. Here's a bit about how the bot works under the hood:

### Collection Scraping

I made the choice to feature these pieces in their full splendor. While you can rely on the image provided by Twitter's preview when you link to your preferred secondary marketplace, you don't want to do this. The intent of the bot is to increase an NFT collection's prominance by showcasing art with every sale. Rest easy knowing that you can still incorporate links without adding a preview if an image is attached. The only problem is that you'll have to collect every photo, and I don't recommend right-clicking to save every file.

That's where my scraper and verify python scripts come into play. They allow you to first take the image URI information and find the token's metadata. From there the metadata is parsed until we identify the image hash and make a 2nd get request to download the image itself. Each file is downloaded synchronously and it takes a while to complete downloads using this method due to how many calls need to get made.

However, If the image URI contains the direct hash of the image you can use a single cURL command to download them all into whatever folder you call the command from:

```
curl -o "MyImages #1.png" https://bafybeibllqyrhmwqwjlaqdu.ipfs.dweb.link/[1-1000].png
```

It's a much faster process, but not many artists seem to prefer doing things this way. It's much more common to get metadata only on your first IPFS request. It's also worth noting that not all browsers can resolve an ipfs address, so I advise using brave browser (links rendered similar in command above) and/or `https://ipfs.io/ipfs/` as the base for URL when making IPFS/HTTP requests. After all of the files are downloaded use the verify.py script to confirm whether any images are missing from your series' image folder.

### Local Development

- Using a Moralis.io server and their SDK, I created a websocket listner that tracks blockchain transfers based on the token's contract address, and the value traded in Ethereum.
- In order to avoid working with an additional database component, I use my API credentials to pull the last block number from a previous tweet if it contains the string "SOLD" in all-caps. I use a loop to avoid tweets that are unrelated.
- Once the block number has been parsed from the previous tweet, I fill an array called `hopper` with all transactions up to the previous block number.
- Each transaction in the hopper is drafted into a tweet based on a variety of conditions including address information and price levels. Then each tweet is posted individually starting with the oldest sale in the list so that the newest is most recent.
- Rinse & Repeat every 30 seconds.

### Remote Hosting

This bot is hosted on AWS using an EC2 Instance for an Ubuntu Web Server using Node.js. It comes with pm2 pre-installed and that allows us to run our program as a background process requiring no front-end user, also known as a daemon. We can run multiple bots off of this one EC2 instance. It just requires you to state which files should be ran within your server. The individual bot only requires one file to run called `client.js`. If you want to list which services are running on pm2 use the command `pm2 list`, to start the bot use `pm2 start client`, and to stop it use `pm2 stop client`.

All of the files are uploaded using an ssh connection and the scp command in bash. Below is an example that transfers all files within the images folder to the matching remote directory.
`scp -i ~/.ssh/myssh.pem c:/webs/NiftyBot/images/* ubuntu@ec2-12-345-678-901.us-east-2.compute.amazonaws.com:NiftyBot/images/`

For Newbies: Once uploaded run npm install to install the dependencies, similar to if it was being ran locally. Do not attempt to transfer a node_modules or .git folder via scp. If you want version control on your server files clone the repo directly into the server instead.

#### Intended Future Updates

- Include sales price in USD
- Report transactions paid in USDC, USDT, DAI, or Wrapped Ether (WETH).
