---
title: 'Superscript Tag &lt;sup&gt; and Line Height'
author: kaela
layout: post
permalink: /snippets/css/superscript-tag-sup-line-height/
categories:
  - css
---
Using \<sup> is really useful when you're dealing with trademarks. Most of the time, you probably won't run into any issues, and the default styles will work perfectly for you. Unless you are using the superscript tag in a title that you'd like aligned with another title tag. For example, maybe you have two columns:

![Wrong way to use the sup tag]({{ site.baseurl }}/images/2014/10/sup_nope.jpg)

Welp, that just doesn't work. Now the spacing is all screwy. Not to worry; three lines of CSS will fix that for you:

<pre class="language-css"><code>sup {
  vertical-align: top;
  position: relative;
  top: -0.3em;
}
</code></pre>

...which results in:

![Wrong way to use the sup tag]({{ site.baseurl }}/images/2014/10/sup_yup.jpg)

line-height: perfect;

## Alternatively...
If you like to keep this kind of stuff controlled by css, use this:

<pre class="language-html"><code>&lt;h2  class="trademark">Join SKECHERS Elite&lt;/h2>
</code></pre>

<pre class="language-css"><code>.trademark:after {
  content: "\2122";
  display: inline-block;
  margin-right: -1px; margin-left: 1px;
  position: relative; top: -0.1em;
}
</code></pre>
