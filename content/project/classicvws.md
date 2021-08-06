---
title: "Classic VW Restorations"
date: 2021-04-15T19:14:07-08:00
hero: ../../images/ClassicVWs.JPG
draft: false
authors:
    - Alex Stouffer
---
## Project Overview

This Project was created for a local auto shop specializing in Classic Volkswagons out of Fullerton CA. Classicvws.shop is built on WordPress using the popular site builder plugin Elementor Pro, and is hosted on an AWS EC2 Instance using the Bitnami Wordpress AMI. 

### Development
1. Created a custom post type for projects as a plugin using a GenerateWP template.
2. Activated Elementor license and updated stock templates for archive lists and single pages.
3. Created a custom front page template based off Adobe XD design approved by client.
4. Created a custom estimation form using styles from the approved front page.

### Migration

1. Once the bitnami instance was live I overwrote the database. My project's database was exported from the localhost phpmyadmin GUI as a .sql file and I imported it to the EC2 instance via SSH and SCP commands.
2. I had to clear the WP-Contents folder on the server using `sudo rm -r path/to/wp-contents/*` so that the git repo may be cloned into the directory without error (must be empty).
3. The instance doesn't include git by default, so I used `sudo apt-get install git`.
4. use `git clone path/to/repo.git .` to clone the contents of the repo into the working directory of wp-content without including the parent repo folder itself.
5. Make sure to associate an elasticIP before pointing a Domain Name at the incstance's public IP. Create an 'A Record' with your host '@' pointed at your public IP address. 

### Version Control/CSS Rendering Issues Using Elementor Pro

Using git as a hub, all of the of the changes were intended to be pushed from a local development and pulled from our EC2 instance. That seemed to not be the case though as changes that were deleted from templates in the localhost showed up on the live server no matter how many times the git repo was updated. I was able to fix this issue on the live server by updating Elementor's CSS Print Method under: Admin Panel->Elementor->Settings->Advanced. In hindsight, if I were to change this setting in the localhost instance it may make the necassary changes in the git repo.
