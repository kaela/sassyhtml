---
title: Installing WordPress Plugins Locally
author: kaela
layout: post
permalink: /snippets/wordpress/installing-wordpress-plugins-locally/
categories:
  - wordpress
tags:
  - install locally
  - install plugins
  - install plugins local
  - wordpress
---
If you are working on your WordPress locally, before uploading it for the world to see, thank you. If you are new to this, there are a few changes you will need to make in order to get everything working properly.

### Installing Plugins Locally

If you try to install themes on default, you will get this:

![Failed plugin download]({{ site.baseurl }}/images/2014/03/plugin-failed.png)

It looks similar to the success message, but if you read through it, you'll see that it failed.

Fortunately, it's a simple fix. In your WordPress directory, set privileges for everyone to "Read & Write" for wp-content/plugins.

![Failed plugin download]({{ site.baseurl }}/images/2014/03/plugin-success.png")

### Adding Media Locally

Similar to plugins, adding media to your localhost will fail on default. Again, it's a pretty easy fix. In your WordPress directory, set privileges for everyone to "Read & Write" for wp-content. 

### Recap

To make plugins and media work on your localhost, set the following directories to have "Read & Write" privileges for everyone:

  * wp-content/plugins
  * wp-content