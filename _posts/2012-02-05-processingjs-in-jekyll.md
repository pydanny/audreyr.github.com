---
layout: post
title: Processing.js in Jekyll
---

{{ page.title }}
================

Do you have a Jekyll blog?  Want to include a <a href="http://processingjs.org">Processing.js</a> sketch into a single post?  This is the quick and dirty way to do it.

PDE sketch in another file
--------------------------

The standard way (in 1.3.6) of using Processing.js is to put all your drawing code into a separate .pde file, rather than embedding it into the page.

You then load the file by putting this into your template:

    <script src="/js/processing-1.3.6.min.js"></script>
    <canvas data-processing-sources="/processing/and-it-works.pde"></canvas>

The .pde file contains the following code:

    void setup() {
        size(580, 400);
        background(100);
        stroke(255);
        ellipse(50, 50, 25, 25);
        println("...and it works!");
    }

The end result is this sketch, with the console window below:

<script src="/js/processing-1.3.6.min.js"></script>
<canvas data-processing-sources="/processing/and-it-works.pde"></canvas>

