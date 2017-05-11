---
layout: post
category: post
title: JS hair pulling
published: true
---

# JS hair pulling #

Didn't think it would take me this long to make this page. I would think it would be a mile long by now. I am bald though, so that should be an indicator.

<hr class="rule">
***

## Bootstrap ease to anchor conflict with carousel ##

This works great, that is unless you have to anchor somewhere other than your page.

```
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
```

Switch out the top line single out a **specific ID**. Look to the `:not([href=#])'`

```
$('a[href*=#]:not([href=#id-of-your-thing])').click(function() {
```

Switch out the top line to allow multiple **bootstrap carousels**.

```
$('a[href*=#]:not([href=#]):not(.carousel-control)').click(function () {
```

Switch out the top line to allow multiple **bootstrap tabs**.

```
$('a[href*=#]:not([href=#]):not([data-toggle="tab"])').click(function () {
```

***
***

## Close Bootstrap mobile nav after click ##

```
jQuery(document).ready(function($) {

  $(".navbar-nav li a").click(function (event) {
      // check if window is small enough so dropdown is created
      var toggle = $(".navbar-toggle").is(":visible");
      if (toggle) {
        $(".navbar-collapse").collapse('hide');
      }
    });

});
```

***
***

## Vanilla JS add CSS to div onClick ##

This chunk was for a nav button to trigger an overlay menu. The overlay *then* had a button in the container to close itself. This is one way to do it without JQuery and seems to work in a pinch.

```
<!-- The HTML -->

    <!-- The open button -->
    <div onclick="openNav()">
      The open button
    </div>

    <div id="customNav">
      <!-- The close button -->
      <a href="javascript:void(0)" class="closebtn" onclick="closeNav()"><span onclick="openNav()">The close button</span></a>
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

```

Plainly speaking, this just adds the CSS "opacity:1.0;" to the "customNav" div when the "openNav" item is clicked, then changes the CSS to "opacity:0;" when the closeNav item is clicked. So pretty brute force, but certainly simple. If you want to send several styles through just repeat the lines like so.

```
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
```

And so on.

***
***

## Hide and go seek nav ##

Wanna hide the nav when you scroll down, then reveal it when you scroll up? Sound like a stupid and annoying idea? That's what I thought.

Let's begin.

Don't ask me what the fuck is going on with this really, but it is marked up by a nice person.


```
$(document).ready(function(){

      // Hide nav

      var didScroll;
      var lastScrollTop = 0;
      var delta = 5;
      var navbarHeight = $('.main-menu').outerHeight();

      $(window).scroll(function(event){
        didScroll = true;
      });

      setInterval(function() {
          if (didScroll) {
              hasScrolled();
              didScroll = false;
          }
      }, 250);

      function hasScrolled() {
          var st = $(this).scrollTop();

          // Make sure they scroll more than delta
          if(Math.abs(lastScrollTop - st) <= delta)
              return;

          // If they scrolled down and are past the navbar, add class .nav-up.
          // This is necessary so you never see what is "behind" the navbar.
          if (st > lastScrollTop && st > navbarHeight){
              // Scroll Down
              $('.full-menu').removeClass('nav-down').addClass('nav-up');
          } else {
              // Scroll Up
              if(st + $(window).height() < $(document).height()) {
                 $('.full-menu').removeClass('nav-up').addClass('nav-down');
              }
          }

          lastScrollTop = st;
      }
   });
```

So, generally - this adds a class to latch onto when your nav scrolls past a certain point. Namely, addClass 'nav-up'. So what you do is tweak a little CSS to manuver your nav off screen like so.

```
.full-menu {
  height: 60px;
  position: fixed;
  padding: 10px 0;
  z-index: 999;
  top: 0;
  transition: top 0.2s ease-in-out;
  -webkit-transition: top 0.2s ease-in-out;
  -moz-transition: top 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  width: 100%;
}

.nav-up {
  top: -80px;
}

.nav-down {
  top: 0px;
}
```

Now, it may not be totally necessary to set the .nav-down position to 0, but it's a good redundant measure. Also you can add whatever additional stuff you like. Now you are so cool.

But lest we forget this is **kind of janky on Android**. Basically what happens is the nav will show after the second swipe. **One swipe up** will pull the navbar url field into view, then **the second swipe will display the hidden nav**. So, while not impossible to master - it would most likely be best to ditch it on mobile.

```
/** Ditch this for mobile **/

@media only screen and (max-width : 768px) {
    .nav-up {
      top: 0;
    }
}
```

***
***

## Using Waypoints and Animate.css? ##

This works for now.

```
$('.fadeinup').addClass('opacity-hidden animated').waypoint({

    handler: function() {
       // Add animate.css classes to .fadeinup
       $(this.element).addClass("opacity-visible fadeInUp")
    },

    // Set the percentage of screen height for trigger
    offset: '80%'
});
```

You may have to one of these if not already in the mix

```
$(document).ready(function(){

  $('.fadeinup').addClass('opacity-hidden animated').waypoint({
     handler: function() {
      $(this.element).addClass("opacity-visible fadeInUp")
    },
      offset: '80%'
  });

});
```

You can also use a toggle like so

```
$('#contact').waypoint({
    handler: function() {
       $('.toggle-color').toggleClass("light-bg")
      },
      offset: '80%'
  });
```

To unpack this one, we choose a class of `fadeinup` that we want to use for our element. Then we are stringing the `opacity-hidden` class (.addClass) first to hide the element on load - otherwise they will hit all at once or flicker, followed by the standard `animated` class to trigger our `animate.css` library. This is capped off as a `.waypoint`.

Finally we are adding the classes of `opacity-visible` and `fadeInUp` to start the `animate.css` animation set by `offset: '80%'`, or when the element is 80% height in the viewport.

CSS like so:

```
/** Hide on the load **/
.opacity-hidden {
  opacity: 0;
  -moz-opacity: 0;
  -webkit-opacity: 0;
}

/** Show for animate.css **/
.opacity-visible {
  opacity: 1.0;
  -moz-opacity: 1.0;
  -webkit-opacity: 1.0;
}
```

HTML like so:

```
<div class="fadeinup">
  <h1>I'm fading up asshole. Everyone's mind is blown</h1>
</div>
```

**Notey note:** You might want to watch out for the `opacity-hidden` class there. But it worked for my hackathon.

***
***
