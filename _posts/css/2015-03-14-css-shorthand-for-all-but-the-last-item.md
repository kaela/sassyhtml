---
title: CSS Shorthand for all but the last item 
author: kaela
layout: post
permalink: /snippets/css/css-shorthand-for-all-but-the-last-item/

categories:
  - css
tags:
  - css
  - navigation
  - last-of-type
  - first-of-type
---

- Targeting a child element is easy: `:last-of-type`
- Targeting all but one element is pretty easy, too: `:not` 
- Chain those together and what do you get? One line of code and less markup in your html!

###There are several different approaches to get this:

<style>
.section-wrap { margin: 15px 30px; }
.navitem:not(:last-of-type) { color: #ed7e2f ; margin-right: 30px;}
</style>

<div class="section-wrap">
  <a href="#" class= "navitem">Home</a>
  <a href="#" class= "navitem">About</a>
  <a href="#" class= "navitem">Thoughts</a>
  <a href="#" class= "navitem">Projects</a>
</div>

But, what's the best way of going about that?

### The dirty HTML / redundant CSS way
Add a class to the last child element:

<pre class="html"><code>
&lt;ul class="section-wrap">
  &lt;li class= "navitem">&lt;a href="#">Home</a></li>
  &lt;li class= "navitem">&lt;a href="#">About</a></li>
  &lt;li class= "navitem">&lt;a href="#">Thoughts</a></li>
  &lt;li class= "navitem last-navitem">&lt;a href="#">Projects</a></li>
&lt;/ul>
</code></pre>

<pre class="css"><code>
.navitem { margin-right: 30px; }
.last-navitem { margin-right: 0; }
</code></pre>

Or...

<pre class="css"><code>
.navitem { margin-right: 30px; }
.navitem.last-navitem { margin-right: 0; }
</code></pre>

The Good:

- This is the fastest way to render your code

The Bad 

- You'll either need to ensure that `.last-navitem` never gets moved before `.navitem` in the css or you're going to need to get more specific:
  - `.navitem.last-navitem`: (not good - we're starting to run into specificity differences)
  - `last-navitem { margin-right: 0!important; }`: Really? I hope you're not using !important on any of your code
- Styles should be handled outside of the html (quoting this bit from [birjolaxew](http://www.reddit.com/user/birjolaxew))
  - html is a structural language
  - The last item is already structured as the last item, simply by being the last item
  - Adding a class to it is redundant and frankly ugly 


### The redundant CSS way

<pre class="html"><code>
&lt;ul class="section-wrap">
  &lt;li class= "navitem">&lt;a href="#">Home</a></li>
  &lt;li class= "navitem">&lt;a href="#">About</a></li>
  &lt;li class= "navitem">&lt;a href="#">Thoughts</a></li>
  &lt;li class= "navitem">&lt;a href="#">Projects</a></li>
&lt;/ul>
</code></pre>

<pre class="css"><code>
.navitem { margin-right: 30px; }
.navitem:last-of-type { margin-right: 0; }
</code></pre>

The Good:

- You're not going to lose *that* much on performance compared to the first example
- Keeps your styles outside of your html

The Bad:

- You define `.navitem`'s styles twice, which causes the browser to repaint (maybe don't put this on a tag used 1000 times throughout the site)


### The shorthand

<pre class="html"><code>
&lt;ul class="section-wrap">
  &lt;li class= "navitem">&lt;a href="#">Home</a></li>
  &lt;li class= "navitem">&lt;a href="#">About</a></li>
  &lt;li class= "navitem">&lt;a href="#">Thoughts</a></li>
  &lt;li class= "navitem">&lt;a href="#">Projects</a></li>
&lt;/ul>
</code></pre>

<pre class="css"><code>
.navitem:not(:last-of-type) { margin-right: 30px; }
</code></pre>

The Good:

- One line of css and no html bloat!

The Bad:

- You define `.navitem`'s styles twice, which causes the browser to repaint (maybe don't put this on a tag used 1000 times throughout the site) (see conclusion for more details on this one)


### Conclusion

At the moment, I'm not sure if there is any difference in performance hit between the second example and this one. If you have any insight, "prey," do tell!

Here's the [codepen](http://codepen.io/kaela/pen/EaOxwR) for the shorthand.