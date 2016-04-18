---
layout: post
title: Common CSS
---

# CSS styles I'm always repeating

I know I have done this a hundred times and have it in all of my basic custom sheets, but for some reason I have to look up this stuff every month or so. Mostly a bunch of Bootstrap stuff and split up for easy chewing.

***
<hr class="rule">

Remove Firefox a outline

<pre>
a {
  outline: 0;
}

a:hover, a:active, a:focus {
  outline: 0;
}

input::-moz-focus-inner {
  border: 0;
}
</pre>

Opacity with IE legacy

<pre>
opacity: 0.5;
-moz-opacity: 0.5;
-webkit-opacity: 0.5;
-o-opacity: 0.5;
filter: alpha(opacity=50);
-ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";
</pre>

Fluid video iframe embed

<pre>
.video-wrapper {
  position: relative;
  /** 16:9 **/
  padding-bottom: 56.25%;
  padding-top: 25px;
  height: 0;
}

.video-wrapper iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</pre>

Blank Bootstrap vanilla responsive styles

<pre>
/*** === Mobile First Method === ***/

/* Custom, iPhone Retina */
@media only screen and (min-width : 320px) {

}

/* Extra Small Devices, Phones */
@media only screen and (min-width : 480px) {

}

/* Small Devices, Tablets */
@media only screen and (min-width : 768px) {

}

/* Medium Devices, Desktops */
@media only screen and (min-width : 992px) {

}

/* Large Devices, Wide Screens */
@media only screen and (min-width : 1200px) {

}

/*** === Non-Mobile First Method === ***/

/* Large Devices, Wide Screens */
@media only screen and (max-width : 1200px) {

}

/* Medium Devices, Desktops */
@media only screen and (max-width : 992px) {

}

/* Small Devices, Tablets */
@media only screen and (max-width : 768px) {

}

/* ipad Portrait and Landscape */
@media only screen
  and (min-device-width: 768px)
  and (max-device-width: 1024px) {

}

/* Extra Small Devices, Phones */
@media only screen and (max-width : 480px) {

}

/* Custom, iPhone Retina */
@media only screen and (max-width : 320px) {

}

/** Retina specific **/
@media
only screen and (-webkit-min-device-pixel-ratio: 2),
only screen and (   min--moz-device-pixel-ratio: 2),
only screen and (     -o-min-device-pixel-ratio: 2/1),
only screen and (        min-device-pixel-ratio: 2),
only screen and (                min-resolution: 192dpi),
only screen and (                min-resolution: 2dppx) {

}
</pre>
