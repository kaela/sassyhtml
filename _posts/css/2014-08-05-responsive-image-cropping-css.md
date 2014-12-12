---
title: Responsive Image Cropping with CSS
author: kaela
layout: post
permalink: /snippets/css/responsive-image-cropping-css/
categories:
  - css
---
Create a responsive promo banner with a fixed height. Image needs to horizontally crop as the browser width changes.

### Requirements

  * Promo banner should stretch the width of the browser (to the max-width of the website)
  * Left div should have a vertically aligned block of text
  * Right div should have a horizontally aligned image that fills the space
  * Promo banner should have a fixed height
  * Use current grid system

### Final Product

<p data-height="500" data-theme-id="7680" data-slug-hash="Lmdpz" data-default-tab="result" data-user="kaela" class='codepen'>See the Pen <a href='http://codepen.io/kaela/pen/Lmdpz/'>Responsive, Croppable Images</a> by Kaela (<a href='http://codepen.io/kaela'>@kaela</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

### Overview

There are four main components in this tutorial: 

1. Absolute/Relative positioning of elements
2. Hiding the image&#8217;s overflow
3. Left: 50%;
4. A negative left margin on the image

### The image

For this tutorial to work, we need a very (vertically) long image with a (fairly) short height. Mine is 1215 x 407px. The focal point is centered in the middle of this image, with a size of about 440 x 407px. If you are having a hard time visualizing a realistic use case, imagine two individuals modeling the latest-and-greatest spring clothing line, sitting on a beach. The models are in the center of the image (at 440 x 407px), while the beach spans the entire width (1215 x 407px) behind them. 

### The wrapper divs

.promo sets the height. You'll want this to match the height of your image. Mine is 407px. So, height: 407px.

Next, set up two empty divs: .promo-imgWrapper and .promo-textWrapper. Give the image wrapper a width of, say, 33.333% and float it left, and the text wrapper a width of 66.666% and float it right. I am using the framework I built at work, hence the classes "_4x12" and "_8x12". When the browser hits a smaller breakpoint, we'll have the divs stack on top of one another. Personally, I prefer the image to stack on top of the text, so I placed the image wrapper div above the text wrapper div. Stack them however you prefer for that smaller breakpoint. 

### The image divs

.promo-imgWrapper wraps your image. It needs a height of 100% to fill the space we just set with .promo. Set the overflow to hidden. Right now, that image just keeps-on-a-goin off the right side of the page. Overflow:hidden will chop off the right side of the image. *Lookin good, eh?!* Give .promo-imgWrapper a relative position. This sets the div relative to its parent, keeping it on the right side.

On to .promo-img. This is where stuff gets interesting, so pay attention! I have:

<pre class="language-css"><code>
.promo-img {
  position: absolute; 
  top: 0; 
  left: 50%;
  margin-left: -607px;
}
</code></pre>

You will always use this setup: **position: absolute; top: 0; left: 50%;**. However, **margin-left: -607px** will change based on the width of your original image. To get your super special number, divide your image width in half and pop a negative sign in front of it.

This works because your image naturally (ha - as if there's anything *natural* about technology) wants to align to the left. We have set the overflow to hidden, but that image is really hanging off a lot to the right. When we set **position: absolute; top: 0; left: 50%**, the image's left side aligns itself in the middle (50%) of it's parent. Okay, so now we have a huge chunk of white space on the left side of our .promo-imgWrapper div, with a tiny piece of our original image on the right side of the div. That's where our negative-half-size comes into play. By taking half the size of our image, we can slide the image all the way back to where we want with a negative margin. In my case, -607px works splendidly.

### The text divs

There are a few ways to get this to work, but I just gave the parent .promo-textWrapper a height of 100% to fill the space, along with a display of table. Yup, I used a table. In the .promo-text div, I set the display to table-cell and vertically aligned it in the middle. 15px padding is pretty good space for the text.

### Wrap Up

And there you have it! A promo banner that works with our already-in-place grid system. The divs are responsive, and the image centers AND crops itself in our designated image space. If anyone has a different way to accomplish this, let me know!