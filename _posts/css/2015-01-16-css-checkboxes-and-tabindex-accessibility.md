---
title: CSS Checkboxes and tabindex Accessibility
author: kaela
layout: post
permalink: /snippets/css/css-checkboxes-and-tabindex-accessibility/
categories:
  - css
---
Create pure css checkboxes that are also accessibile with tabindex.


### Overview

There are a lot of awesome tutorials that show us how to style inputs. Unfortunatley, many of those tutorials prevent users from tabbing to those new styled inputs, which is a big no-no for accessibility.

Typically, it might go something like this:

~~~ html
<input type="checkbox" id="age" class="toggleInput">
<label for="age" class="checkbox-styled">I am over 18 years of age</label>
~~~

~~~ css
.toggleInput { display: none; }
.checkbox-styled {
    .checkbox-slide:before {
    content: "";
    border: #ccc 1px solid;
    height: 100%;
    width: 40px;
    position: absolute;
    top: 0;
    left: 0;
}
.checkbox-styled:after {
    font-size: 30px;
    font-size: 3rem;
    -webkit-transition: all 0.4s ease;
    -moz-transition: all 0.4s ease;
    -o-transition: all 0.4s ease;
    -ms-transition: all 0.4s ease;
    transition: all 0.4s ease;
    color: #0063ba;
    content: '\2713';
    position: absolute;
    top: -40px;
    left: 0;
    text-align: center;
    width: 40px;
}
.toggleInput:checked + .checkbox-styled:after {
    top: 0;
}
~~~


### The Problem
Tabindex skips right over that hidden input. That's horrible for accessibility. For example, how would a person with poor or zero vision even know that input exists?

Fortunately, it's a pretty easy fix


### The Fix
Change 
`.toggleInput { display: none; }` 
to 
`.toggleInput { position: absolute; opacity: 0; }`

Basically, browsers skip over content that is hidden. This is typically a good thing. For example, you might be hiding elements on smaller screens, and you don't want the user tabbing 5 times before getting to the next visible element. However, in cases where developers are attempting to make ugly inputs pretty, that feature can start looking like a bug. Luckily, there's an easy way to adjust this in our case.
