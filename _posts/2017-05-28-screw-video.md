---
layout: post
category: post
title: Enough with the video
published: true
---

# Video backgrounds, I just... I.. #

I know what you are thinking. So, just stop it already. They want it to happen. Doesn't matter that they *never* work, or that the video will cause seizures. They want it to happen and they saw it happen.

It's gonna happen, just bend over.

<hr class="rule">
***

## Full Screen ##

This one **actually worked**.

Maybe it's not all bad. [You could just do this](http://thenewcode.com/777/Create-Fullscreen-HTML5-Page-Background-Video) and tell them all to fuck off if the browser doesn't support HTML5. It's Not your fault... It's not your fault... It's not your fault...

<pre>
<video playsinline autoplay muted loop poster="/images/die-already.jpg" id="bgvid">
  <source src="die-already.webm" type="video/webm">
  <source src="die-already.mp4" type="video/mp4">
  <source src="die-already.ogg" type="video/ogg">
</video>
</pre>

That's it assholes, and now for the CSS.


	video#bgvid {
      position: fixed;
      top: 50%;
      left: 50%;
      min-width: 100%;
      min-height: 100%;
      width: auto;
      height: auto;
      z-index: -100;
      -ms-transform: translateX(-50%) translateY(-50%);
      -moz-transform: translateX(-50%) translateY(-50%);
      -webkit-transform: translateX(-50%) translateY(-50%);
      transform: translateX(-50%) translateY(-50%);
      background: url(/images/die-already.jpg) no-repeat;
      background-size: cover;
	}

***
***

## In a wrapper ##

<pre>
<div class="wrapper">
  <video playsinline autoplay muted loop poster="/images/die-already.jpg" id="bgvid">
    <source src="die-already.webm" type="video/webm">
    <source src="die-already.mp4" type="video/mp4">
    <source src="die-already.ogg" type="video/ogg">
	</video>
</div>
</pre>

And the CSS

	.wrapper {
      position: relative;
      height: 300px;
      overflow: hidden;
    }

	#bgvid {
      position: absolute;
      top: 50%;
      left: 50%;
      z-index: 1;
      width: 600px;
      height: auto;
      transform: translate(-50%, -50%);
      -moz-transform: translate(-50%, -50%);
      -webkit-transform: translate(-50%, -50%);
      -ms-transform: translate(-50%, -50%);
    }

I have **not done this**.

At least this is the start of it from [this fellah](http://callmenick.com/post/html5-video-jumpstart-examples). You will have to set up your own media queries. This *may* work with the fluid iframe css.

***
***

## Crunch the fuck out of it ##

Now, you will have to hide it for mobile. In order not to have angry mobs at your door, you should smash this thing as much as you can.

VLC will take care of the .webm and .ogg for you. If you **space how to do this**, go to **file > Convert / Stream**. Then choose your format from the dropdown.

Aim for 5MB if you can.

***
***

## Overlay ##

Since your video is smashed, you can use an overlay to ease it's pain. Now when someone makes a screenshot it will look horrific. Huzzah!

	.overlay {
  	  width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
      background: url(/images/overlay.png) repeat;
      /** or whatever z-index that works **/
      z-index: 0;
    }

***
***
