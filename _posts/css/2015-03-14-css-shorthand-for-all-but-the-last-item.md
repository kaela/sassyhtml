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

- Targetting a child element is easy: `:last-of-type`
- Targeting all but one element is pretty easy, too: `:not` 
- Add those together and what do you get? One line of code and less markup in your html:

<pre class="css"><code>.navitem:not(:last-of-type) { whatever-styles-you-want }</code></pre>

### The wrong way
For the longest time, I have been adding a class to the last of my html items, and using the :not selector to style all items except that one, like so:

<pre class="html"><code>&lt;nav>
  &lt;a href="#">Home</a>
  &lt;a href="#">About</a>
  &lt;a href="#">Thoughts</a>
  &lt;a href="#" class= "last-item">Projects</a>
&lt;/nav></code></pre>

<pre class="css"><code>.a { text-decoration: none; }
.a:not(.last-item) { color: #ed7e2f; margin-right: 30px; }</code></pre>

which results in...
<style>
.section-wrap { margin: 15px 30px 45px; }
.navitem { text-decoration: none; }
.navitem:not(.last-navitem) { color: #ed7e2f ; margin-right: 30px; }
</style>

<div class="section-wrap">
	<a href="#" class= "navitem">Home</a>
	<a href="#" class= "navitem">About</a>
	<a href="#" class= "navitem">Thoughts</a>
	<a href="#" class= "navitem last-navitem">Projects</a>
</div>



###Silly me. 
There's an easy shorthand, so I don't have to bloat my html: 

- The :not psuedo-class `+` any child selector. 

Here it is again:

<pre class="css"><code>.navitem:not(:last-of-type) { whatever-styles-you-want }</code></pre>


Now I just need to go clean up my html! If you completely missed this selector combo like me, I hope this helps.

Here's the [codepen](http://codepen.io/kaela/pen/EaOxwR).