---
title: Landing pages for categories using Archives
author: kaela
layout: post
permalink: /snippets/wordpress/landing-pages-categories-using-archives/
categories:
  - wordpress
tags:
  - archives
  - categories
  - landing pages
  - pages
  - wordpress
---
Here is an option for people who are okay with using "categories" as your filing system. You will **ONLY** be able to use this option if you use **ONE** category per post. If you're cool with that, and using tags to incorporate additional labeling, this may be a good option for you. It really doesn't get any easier than this.

Here is an example of a super simple structure for a website:

<pre class="language-wp"><code>- home
-- css
--- de css posts
-- scss
--- de scss posts
-- html
--- de html posts
etc.
</code></pre>

Basically, it goes three "pages" deep:

  1. Set up your categories by going to admin > Posts > Categories
  2. Next, go to Admin > Settings > Permalinks
  3. Select "Custom Structure" and type, "/%category%/%postname%."
  4. Assign each of your posts to **ONE*** category

*If you add more than one category to a post, your post will be filed under: yourdomain/uncategorized/post-title 

You're done! You now set your Archive pages as landing "pages" for each category. To modify those archive pages, edit the archives.php file.

So that's it. Pretty simple, eh? Of course, you have to be willing to use only one category per post, but according to this great article on *[The Right Way to Use Categories and Tags in WordPress to Boost SEO][1]* by Tom Ewer, we should be limiting our posts to one or two categories anyway. 

 [1]: https://managewp.com/wordpress-categories-tags-seo "Read The Right Way to Use Categories and Tags in WordPress to Boost SEO"