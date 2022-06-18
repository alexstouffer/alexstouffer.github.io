---
title: 'Win Clients With Professional Email Signatures'
date: 2022-06-16T00:38:50-07:00
hero: ../../images/email-sig.png
draft: true
authors:
  - Alex Stouffer
---

We always want to approach our sales prospects with the utmost professionalism whether we're working independently or as part of a larger organization. That can be pretty challenging when the best option to present ourself is a cold email. They don't know who we are or our reputation. If a client can't gauge that quickly they will not burn any time to consider our value proposition. However, there are many things we can do to improve our chances with new clients over cold emails. In this post we'll highlight how to create custom email signatures. This valuable addition to your business not only acts as a business card, but as a way to humanize ourselves with a profile picture and engender trust with the complete strangers we hope to begin relationships with.

### Step 1: Create a Design That Best Represents Your Brand

We'll want to consider a few things before we begin our design. We'll want to decide what social media links we want to include on our template besides our basic contact information like name, title, phone number, and email address. We'll also want to consider what colors we want to use in our design. In general I recommend using one color from your company logo and a white background so that the signature 'pops' in your client's email application.

Once all of the information is gathered we can begin designing. I use Figma with design clients so that they can see the updates made in real-time online using a link I send to them. Users added to the project can also write comments and keep them organized without relying on an exhaustive email thread or in-person meeting. Ideally we want our template to be no wider than `600 pixels` and kept under a height of `200 pixels`. Create a few sample designs and get feedback on what suits your organization best while ensuring those designs conform with your brand and style guide (if available).

### Step 2: Upload Your Photos to a Public Folder

Once we have our final design selected, it's time to create a public file repository where we can upload any photos to be included in our email template. I like to use dropbox and if you keep all files under 2GB it's free. Otherwise you can use any service, so long as you can access a link to the photo without being an authenticated user of whatever service you choose. You can confirm that the links work by opening a private browsing tab in Brave or using Incognito Mode in Chrome Browser. If the link is inaccessible, make sure that the link has permissions set where anyone with the link can view the file. Another possible issue is that the link you're given by the service provider isn't set to allow downloads. Check out our example link:

```
https://www.dropbox.com/s/cazd4xjl6h6om69/keys.png?dl=0
```

If you copy this link and paste it in the browswer you'll see blurry set of keys, but this photo wouldn't be viewable in your email template because the `?` query parameter is set as `dl=0`. Zero represents a falsey boolean value in programming, while the number one represents a truthy boolean value. Update the link to say `dl=1`, and your file will now be viewable within your email template.

### Step 3: Create the Template Using HTML Tables and Inline CSS

We're know all set to begin building our functional email signature template. One hiccup in creating email templates is that we cannot use div elements and external style sheets to style our content. We have go incredibly old-school to a time when websites were made mainly with Table layouts and inline CSS. We've moved away from the style of development because of the difficulty in laying out our elements aesthetically. Luckily we now have tools to do this more easily, so we'll want to use an [HTML table generator](https://www.tablesgenerator.com/html_tables) as an aide. This will help us visually observe where our elements might be placed in relation to our design and can also tell us if they need to be placed in table cells that span more than one column or row. For instance, in our example the profile photo spans two rows so that directly to the right of it we have the top row represent our name and title, while the row below that contains our contact information. This keeps us from crowding elements in one particular table cell.

A useful tip when using a Table Generator is to create a row that only represents your background color and have it span all columns. That way the row underneath it can lay over the top of that background color when styled appropriately using the `position` attribute.

### Step 5: Add the Signature in Your Email Service Provider

Now that you have your template it's time to add it to our email client. If your client allows for direct input of HTML use that. Otherwise open your template `.html` file in a browser window and press `CTRL + A` to select everything on the page before copying, and then paste it into your email signature field. Click save and test your email out to ensure that you're all good to go.[Google](https://support.google.com/mail/answer/8395?hl=en&co=GENIE.Platform%3DDesktop) and [Outlook](https://support.microsoft.com/en-us/office/create-an-email-signature-31fb24f9-e698-4789-b92a-f0e777f774ca) have specific directions available for their email services.

### What if I have multiple signatures I need made?

It's possible to use a spreadsheet of employee information and a custom script to input each employees information into its own rendered template. It can be a pretty daunting task, if you're not familiar at all with writing code. If that's the case, please reach out to me for help.

I offer a complete package covering design, revisions, development, and scripting for a flat rate of $1000 USD for the first 100 employees. Additional employees are $10 for each thereafter, with options to add a form generating new & consistent signatures for every employee you hire moving into the future.

Don't let poor presentation be the reason you missed out on a sale. Schedule your free consultation today!
