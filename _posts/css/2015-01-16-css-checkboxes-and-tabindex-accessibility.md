---
title: CSS Checkboxes and Tabindex Accessibility
author: kaela
layout: post
permalink: /snippets/css/css-checkboxes-and-tabindex-accessibility/
categories:
  - css
---
Create pure css checkboxes that are also accessibile with tabindex.

<section class="embeddedCode">
    <p data-height="100" data-theme-id="7680" data-slug-hash="XJMwyo" data-default-tab="result" data-user="kaela" class='codepen'>See the Pen <a href='http://codepen.io/kaela/pen/XJMwyo/'>XJMwyo</a> by Kaela (<a href='http://codepen.io/kaela'>@kaela</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
    <script async src="//assets.codepen.io/assets/embed/ei.js"></script>
</section>

### Overview

There are a lot of awesome tutorials that show us how to style inputs. Unfortunatley, many of those tutorials prevent users from tabbing to those new styled inputs, which is a big no-no for accessibility.

Typically, it might go something like this:

<pre class="language-html"><code>
&lt;input type="checkbox" id="age" class="toggleInput">
&lt;label for="age" id="label-age" class="checkbox-slide">Check me - I slide&lt;/label>
</code></pre>

<pre class="language-css"><code>
.toggleInput { position: absolute; opacity: 0; }

.checkbox-slide {
  -webkit-transition: all 0.4s ease;
  -moz-transition: all 0.4s ease;
  -o-transition: all 0.4s ease;
  -ms-transition: all 0.4s ease;
  transition: all 0.4s ease;
  cursor: pointer;
  display: block;
  line-height: 40px;
  overflow: hidden;
  padding-left: 50px;
  position: relative;
  width: 100%;
}

.checkbox-slide:before {
  content: "";
  border: #ccc 1px solid;
  height: 100%;
  position: absolute; top: 0; left: 0;
  width: 40px;
  
}

.checkbox-slide:after  {
  font-size: 30px;
  -webkit-transition: all 0.4s ease;
  -moz-transition: all 0.4s ease;
  -o-transition: all 0.4s ease;
  -ms-transition: all 0.4s ease;
  transition: all 0.4s ease;
  color: #0063ba;
  content: '\2713';
  position: absolute; top: -40px; left: 0;
  text-align: center;
  width: 40px;
}

.toggleInput:checked + .checkbox-slide:after  { top: 0; }
</code></pre>


### The Problem
Tabindex skips right over that hidden input. That's horrible for accessibility. For example, how would a person with poor-to-zero vision even know that input exists?

Fortunately, it's a pretty easy fix


### The Fix
Change 

<pre class="language-css"><code>
.toggleInput { display: none; }
</code></pre> 
to 

<pre class="language-css"><code>
.toggleInput { position: absolute; opacity: 0; }
</code></pre>

Basically, browsers skip over content that is hidden. This is typically a good thing. For example, you might be hiding elements on smaller screens, and you don't want the user tabbing 5 times before getting to the next visible element. However, in cases where developers are attempting to make ugly inputs pretty, that feature can start looking like a bug. Luckily, there's an easy way to adjust this in our case.
