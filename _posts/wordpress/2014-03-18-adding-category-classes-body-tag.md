---
title: Adding category classes to body tag
author: kaela
layout: post
permalink: /snippets/wordpress/adding-category-classes-body-tag/
categories:
  - wordpress
tags:
  - add class
  - body
  - body classes
  - category
  - category classes
  - classes
---
Trying to add category classes was a bit tedious. I ran across a few blog posts on how to implement them. Many didn't work (maybe they were for previous versions of WordPress?), but one did.

### What worked

<pre class="language-php"><code>
add_filter('body_class','add_category_to_single');

function add_category_to_single($classes) {
  if (is_single() ) {
    global $post;
    foreach((get_the_category($post->ID)) as $category) {
      echo $category->cat_name . ' ';
	  
      // add category slug to the $classes array
      $classes[] = 'category-'.$category->slug;
    }
  }
  // return the $classes array
  return $classes;
}
</code></pre>

Reference: [jackreichert][1]

### What did not work

<pre class="language-php"><code>
add_filter('body_class','add_category_to_single');
function add_category_to_single($classes, $class) {
  if (is_single() ) {
    global $post;
    foreach((get_the_category($post->ID)) as $category) {
      echo $category->cat_name . ' ';
      
      // add category slug to the $classes array
      $classes[] = 'category-'.$category->slug;
    }
  }
  // return the $classes array
  return $classes;
}
</code></pre>

This looks REALLY close to the working code, but the function properties includes a second function value, "$class", which outputs the following error:

<pre class="language-html"><code>
Warning: Missing argument 2 for add_category_to_single() in /home/tonguet1/public_html/wp-content/themes/TTM/functions.php on line 6
News class="single postid-493 logged-in category category-news">
</code></pre>

Not sure what's happening there, but just remove that second value.

### This also didn't work

<pre class="language-html"><code>
<body id="top" &lt;?php if (function_exists('body_class')) body_class('category-'.$class ); ?>
</code></pre>

Instead of adding the category class, it just adds "category-" so it isn't really helpful. If you use this along with the snippet posted above, it will add an additional class of "category" which again, isn't helpful.

Hope this helps everyone else from spending 15min searching for the right code.

 [1]: http://wordpress.org/support/topic/php-issue-once-uploaded-to-server#post-1551522