---
layout: post
title: Jekyll Blog Posts With Custom CSS
---

<style type="text/css">
.flower{width:100px;height:100px;color:red;}
</style>

{{ page.title }}
================

How do you include custom CSS in a Jekyll blog post without using inline CSS styles?

Why would you want to do this, anyway?  Well, suppose you're trying to demo some interersting CSS code that you've written.  Suppose your code uses CSS pseudo-elements.  

You might think you're out of luck, since:

* you can't apply CSS pseudo-elements inline
* you can't modify anything within `<head>` from your Jekyll post
* you can't select pseudo-elements with jQuery because they're not part of the DOM.

But wait! It's a hack, but you can append a `<style>` element to `<head>`.  The code looks like this:

    
    <div class="box"></div>

    <script type="text/javascript">
    {% highlight JavaScript %}
    $(function() {
        $('<style>.box:before{ \
            background-color:#ED4C8D; \
            content:"#"; \
            color:white; \
            display:block; \
            width:80px; \
            height:100px; \
        }</style>').appendTo('head');

        $(".box").css({
            'background-color': '#4CEDE2', 
            'width': '100', 
            'height': '120'
        });
    {% endhighlight %}
    </script>
    

And the resulting box div looks like this:

<div class="box"></div>

<script type="text/javascript">
$(function() {
    $('<style>.box:before{ \
            background-color:#ED4C8D; \
            content:"#"; \
            color:white; \
            display:block; \
            width:80px; \
            height:100px; \
        }</style>').appendTo('head');
    
    $(".box").css({
        'background-color': '#4CEDE2', 
        'width': '100', 
        'height': '120'
    });
});
</script>