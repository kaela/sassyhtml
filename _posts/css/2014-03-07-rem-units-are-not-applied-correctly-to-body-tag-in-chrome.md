---
title: REM units are not applied correctly to body tag in Chrome
author: kaela
layout: post
permalink: /snippets/css/rem-units-are-not-applied-correctly-to-body-tag-in-chrome/
categories:
  - css
tags:
  - chrome
  - css
  - "doesn't work in chrome"
  - em
  - font-size
  - not working
  - not working in chrome
  - px
  - rem
---
[Track this issue](https://code.google.com/p/chromium/issues/detail?id=319623) on chromium. It was closed back in January, but it still occasionally happens for me.

### rem fans like to use this*, but Chrome doesn&#8217;t like it:

<pre class="language-css"><code>html { font-size: 62.5%; } 
body { font-size: 1.4rem; } 
h1   { font-size: 2.4rem; } 
</code></pre>

*a magical snippet from [Jonathan Snook](http://snook.ca/archives/html_and_css/font-size-with-rem) 

We use 62.5% on the html to bring the base font down to 10px, for easy multiplication. Then, the rest is SUPPOSED to be easy. That body font-size should 1.4rem * 10px = 14px. The h1 should have a font-size of 24px.

### What actually happens in Chrome (about 50% of the time):

Chrome will not let you set that base font below 100% (16px). Well, sometimes it does. But sometimes it doesn't. Check out what happens to the body and h1 font sizes. 

<pre class="language-css"><code>html { font-size: 62.5%; }
body { font-size: 1.4rem; } /* 1.4 * 16 = 22.4px */
h1   { font-size: 2.4rem; } /* 2.4 * 16 = 38.4px */
</code></pre>

Since we tried setting that root font-size below 100%, or 16px, Chrome reverted back to using 16px as the root font size.

### Fix it like this:

Fortunately, the workaround is pretty simple. The actual issue here is the rem. So, set the body font size with em. Since the body tag is generally dependent on the root/html, there should be no cascading issues. 

<pre class="language-css"><code>body {font-size: 1.4em;} 
</code></pre>

or this

I'm not a huge fan of these next two options. They do work, but they seem messy, especially the last one. I really don't like applying styling to * (aside from the limited amount I use for reset).

<pre class="language-css"><code>* {font-size: 1.4rem;} 
</code></pre>

or this

You could replace `<div>` with whatever you use for your wrapper

<pre class="language-css"><code>body > div {font-size: 1.4rem;} 
</code></pre>