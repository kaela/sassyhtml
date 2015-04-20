---
title: HTML that Responds Like Images
author: kaela
layout: post
permalink: snippets/css/html-that-responds-like-images/
categories:
  - css
tags:
  - css
  - responsive
  - images
  - stretch
  - responsive design
---

Adjust your browser's width and watch the following block of content respond vertically and horizontally.

<div class="parent">
  <div class="left post-image respond">
    <img src="http://www.dumpaday.com/wp-content/uploads/2013/01/funny-cat-bath.jpg">
  </div>
  <div class="right description respond">
    <h1>What the heck</h1>
    <p>I respond too?!</p>
  </div>
</div>

### Grok this
- Padding and margin are based on the parent container's width ([official css box model specs](http://www.w3.org/TR/CSS2/box.html#margin-properties)) 
- This is true for **all four sides** of padding and margin (top, right, bottom, and left)

When using pixels, this obviously isn't an issue. However, this tutorial uses percentages, so you need to understand the css box model specs in order to understand why this technique works.



### Overview
- Use only percentages to keep everything responsive
- Set the height of our responsive elements to zero in order to avoid using px
- Aspect ratio = height / width


### The math
I want my image to take up **25%** of the screen's width. I want the content to take up 75% of the screen's width. The original size of the image is **620** x **822**.

- (image height / image width) * 100 * % element takes up in your grid
- (822 / 620 ) * 0.25 = 0.33 
- Both the image and content elements will use padding-bottom: 33%

### Still with me?
If all of this makes sense to you, feel free to skip the rest. If it's still a little iffy, keep reading for a further explanation. 

### Example

<p data-height="470" data-theme-id="7680" data-slug-hash="MYNNBg" data-default-tab="css" data-user="kaela" class='codepen'>See the Pen <a href='http://codepen.io/kaela/pen/MYNNBg/'>MYNNBg</a> by Kaela (<a href='http://codepen.io/kaela'>@kaela</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

### Height of Zero
Take a look at the height of the child elements, `.left` and `.right`. Using a height will mess up our responsive elements since height uses a static unit, like px. So we will set that to zero.

### How the Browser Calculates Padding
In order to simplify things, let's say our site is not responsive. This is what we have in our site: 

- One container div, `.parent`, which is 800px wide
- Inside of `.parent`, there are two children, `.left` and `.right`. 
- `.left` is 25% wide
- `.right` is 75% wide
- Both children have a padding-bottom of 33%

Let's convert everything to px to see clearly how this all works:

- `.parent` (max-width) = 800px
- `.left` = 25% = 200px
- `.right` = 75% = 600px

So what do you think the padding will be, in pixels?

If you guessed 264px, you're right! To calculate the padding, we use 800px * 0.33, which is 264px.

Of course, our site is responsive and the width does change. And that is exactly why were are using percentages.


### Using Aspect Ratio

If you are using this technique with an image, you will need to base your padding-bottom on the aspect ratio of that image. This ensures you're not cropping out parts of the image or adding unnecessary spacing below it.

The image above has an original height of 822px and a width of 620px. 

Aspect ratio = height/width = 822/620 = 1.32. But that number won't work for us as-is, because our image isn't taking up 100% of the screen’s width.

Our image is inside of the `.left` div, which is taking up 25% of the screen’s width. So, we need to multiply our aspect ratio by 0.25: 1.32 * 0.25 = 0.33. 

33% is the number we need to use in order to keep our image looking spiffy at every browser size.

We also need to that padding of 33% to the `.right` div. Remember earlier, when I showed you the [css box model specs](http://www.w3.org/TR/CSS2/box.html#margin-properties), and how padding is based on the parent element's width? That means each child element needs the same padding-bottom to remain the same height. Feel free to play with my codepen above. It looks pretty funky when you don’t keep the padding the same.

### Another use case
This could be used for missing images from the database. One way to implement this is to add some javascript and css love. If the image is there, show it. If not, apply a class. No need for an additional image.

<pre class="language-css"><code>.missingImage {
  // only the following two styles are required
  height: 0;
  padding-bottom: 88%; //aspect radio in % * parent div’s width in %

  //some optional styling below
  border: $accent 5px solid;
  position: relative;
  &:after {
    color: $gray-med;
    content: "Missing Image";
    margin-top: -8px;
    position: absolute; top: 50%;
    text-align: center;
    width: 100%;
  }
}
</code></pre>
