---
layout: post
category: post
title: JS Hair Pulling
published: true
---

# JS Hair Pulling #

Didn't think it would take me this long to make this page. I would think it would be a mile long by now. I am bald though, so that should be an indicator about this.

<hr class="rule">
***

## Bootstrap ease to anchor conflict with carousel ##

This works great, that is unless you have to anchor somewhere other than your page.

<pre>
<code>
jQuery(document).ready(function($) {

  $('a[href*=#]:not([href=#])').click(function() {
    if (location.pathname.replace(/^\//,'') == this.pathname.replace(/^\//,'') && location.hostname == this.hostname) {
      var target = $(this.hash);
      target = target.length ? target : $('[name=' + this.hash.slice(1) +']');
      if (target.length) {
        $('html,body').animate({
          scrollTop: target.offset().top
        }, 250);
        return false;
      }
    }
  });

});
</code>
</pre>

Switch out the top line to change for a specific ID. Look to the `:not([href=#])'`

    $('a[href*=#]:not([href=#id-of-your-thing])').click(function() {

Switch out the top line to allow multiple carousels or other JS options.

    $('a[href*=#]:not([href=#]):not(.carousel-control)').click(function () {

***

## Close the Bootstrap mobile nav after click ##

<pre>
<code>
jQuery(document).ready(function($) {

	$(".navbar-nav li a").click(function (event) {
    // check if window is small enough so dropdown is created
    var toggle = $(".navbar-toggle").is(":visible");
    if (toggle) {
      $(".navbar-collapse").collapse('hide');
    }
  });

});
</code>
</pre>
