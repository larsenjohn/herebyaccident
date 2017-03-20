---
layout: post
category: post
title: JS Hair Pulling
published: true
---

# JS Hair Pulling #

Didn't think it would take me this long to make this page. I would think it would be a mile long by now. I am bald though, so that should be an indicator.

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

Switch out the top line single out a specific ID. Look to the `:not([href=#])'`

    $('a[href*=#]:not([href=#id-of-your-thing])').click(function() {

Switch out the top line to allow multiple carousels or for other JS options.

    $('a[href*=#]:not([href=#]):not(.carousel-control)').click(function () {

<hr class="rule">
***

## Close Bootstrap mobile nav after click ##

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

<hr class="rule">
***

## Vanilla JS add CSS to div onClick

This was for a nav button to trigger and overlay. The overlay then had a button in the container to close itself. I guess this is the only way to do this without JQuery, but it seems to work in a pinch.

<pre>
<code>
<!-- The HTML -->

	<!-- The open button -->
	<span class="ti-menu" onclick="openNav()"></span>
    
    <div id="customNav">
    	<!-- The close button -->
		<a href="javascript:void(0)" class="closebtn" onclick="closeNav()"><span class="ti-close" onclick="openNav()"></span></a>
    
    	<p>The shit inside the div</p>
    </div>

<script>
function openNav() {
	document.getElementById("customNav").style.opacity = "1.0";
}

function closeNav() {
	document.getElementById("customNav").style.opacity = "0";
}
</script>
</code>
</pre>

Plainly speaking, this just adds the following CSS to the customNav div. So pretty brute force but certainly simple. If you want to send several styles through just repeat the lines like so.

<pre>
<code>
<script>
function openNav() {
	document.getElementById("customNav").style.opacity = "1.0";
	document.getElementById("customNav").style.visibility = "visible";
}

function closeNav() {
	document.getElementById("customNav").style.opacity = "0";
	document.getElementById("customNav").style.visibility = "hidden";
}
</script>
</code>
</pre>

And so on.

<hr class="rule">
***
