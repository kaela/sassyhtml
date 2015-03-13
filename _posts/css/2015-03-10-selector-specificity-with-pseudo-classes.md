---
title: Selector Specificty with Pseudo-Classes
author: kaela
layout: post
permalink: /snippets/css/2015-03-10-selector-specificity-with-pseudo-classes
categories::
  - css
---

Order of importance:

1. h1:not(.className) 
2. .className 
3. h1


### Not sure how I missed this
[According to Mozilla](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity), this is the ascending specificity, in order starting at the most specific:

1. Inline style
2. ID selectors
3. Pseudo-classes
4. Attributes selectors
5. Class selectors
6. Type selectors
7. Universal selectors

I think most of us have figured this out. I mean, that's why a lot of us have decided to avoid styling on IDs. Whatever you style on the ID overrides anything you have on the class. It makes specificity a mess. But a lot of us still style a typography.scss file (or something similar). Inside, we style headings and paragraphs, etc. And sometimes you might want to address all section titles *except* those on, say, the Thank You page. So you have your html for your thankyou.html as:

<pre class="language-html">
<code>
&lt;h2 class="thankyouTitle">My Cool Section Title&lt;/h2>
</code>
</pre>

and your css is:
<pre class="language-css"><code>
    h2:not(.thankyouTitle) { font: standardFont; }
    .thankyouTitle         { font: coolSpecialFont; margin: 0 auto; }
    h2                     { font-size: 3rem; font-weight: bold; margin: 15px; }
</code></pre>

Great, so everything looks good. You've got most h2s using the standard font, which has 15px margins. Your Thank You page h2s will have the new cool font and the 





### :not
The :not psuedo selector. It has come in pretty handy to me on a few occassions. For those of you new to psuedo selectors, `:not` is used to select everything *except* whatever selector you specify:

<pre class="language-css"><code>
.bookTitles:not(.redBooks) { color: blue; }
</code></pre>

In the example above, all book titles will have red font except for those with the class of .redBooks.

### 
