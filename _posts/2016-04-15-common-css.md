---
layout: post
category: post
title: Common CSS
published: true
---

# CSS styles I'm always repeating

I know I have done this a hundred times and have it in all of my basic custom sheets, but for some reason I have to look up this stuff every month or so. Mostly a bunch of Bootstrap stuff and split up for easy chewing.

***
<hr class="rule">

Remove Firefox `<a>` outline

    a {
      outline: 0;
    }

    a:hover, a:active, a:focus {
      outline: 0;
    }

    input::-moz-focus-inner {
      border: 0;
    }

Opacity with IE legacy

    opacity: 0.5;
    -moz-opacity: 0.5;
    -webkit-opacity: 0.5;
    -o-opacity: 0.5;
    filter: alpha(opacity=50);
    -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";

Simple vanilla CSS3 ease

    transition: all 0.15s ease-in-out;
    -webkit-transition: all 0.15s ease-in-out;
    -moz-transition: all 0.15s ease-in-out;
    -o-transition: all 0.15s ease-in-out;

Wrap an `<a>` tag around a div.


    <div class="wrap">
      <a class="link-full-div" href="#"></a>
        <h1>Link the entire div</h1>
        <p>Content</p>
    </div>

    .wrap {
      position: relative;
    }

    a.link-full-div {
      position: absolute;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
      text-decoration: none;
      z-index: 999;
    }

Fluid video `iframe` embed.

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


Absolute center fluid container

	.parent {
	  position: relative;
	}
	
	.child {
	  position: absolute;
	  top: 50%;
	  left: 50%;
	  transform: translate(-50%, -50%);
	  -moz-transform: translate(-50%, -50%);
	  -webkit-transform: translate(-50%, -50%);
	  -ms-transform: translate(-50%, -50%);
	}

Bootstrap vanilla media queries


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

Jotform reset to 100% width. Good starting place for simple forms w/Google fonts.

    /** Jotform Reset **/

    /** import fonts @top or pull them for default **/
    @import ... Google font

    .form-all {
      /* Define font family */
      font-family: 'Google font', serif;
      font-weight: 400;
      color: #4d4d4d;
      padding-top: 0;
    }

    input,
    textarea {
      font-family: 'Google font', serif;
      font-weight: 400;
      width: 100%;
      min-width: 100%;
      padding: 8px !important;
      /* box sizing */
      box-sizing: border-box !important;
      -moz-box-sizing: border-box !important;
      -webkit-box-sizing: border-box !important;
      -o-box-sizing: border-box !important;
      /* cut border radius */
      border-radius: 0 !important;
      -webkit-border-radius: 0 !important;
      -moz-border-radius: 0 !important;
      -o-border-radius: 0 !important;
      /* Appearance */
      appearance: none !important;
      -webkit-appearance: none !important;
      -moz-appearance: none !important;
      -o-appearance: none !important;
      /* Cut box shadow */
      box-shadow: none !important;
      -webkit-box-shadow: none !important;
      -moz-box-shadow: none !important;
      -o-box-shadow: none !important;
      background: #ffffff !important;
      outline: none !important;
    }

    *, *:before, *:after {
      box-sizing: border-box;
      -webkit-box-sizing: border-box;
      -moz-box-sizing: border-box;
      -o-box-sizing: border-box;
    }

    .form-line-error {
      background: none;
    }

    .form-line {
      padding-top: 5px;
      padding-bottom: 10px;
      padding-left: 0;
      padding-right: 0;
      width: 100%;
    }

    .form-input .form-error-message,
    .form-input-wide .form-error-message {
      padding-top: 10px;
      padding-right: 10px;
      padding-bottom: 10px;
      padding-left: 10px;
      /* cut border radius */
      border-radius: 0;
      -moz-border-radius: 0;
      -webkit-border-radius: 0;
      -o-border-radius: 0;
      /* cut box-shadow */
      box-shadow: none;
      -webkit-box-shadow: none;
      -moz-box-shadow: none;
      -o-box-shadow: none;
    }

    .form-input .form-error-message img,
    .form-input-wide .form-error-message img {
      display: none;
      height: 0;
      width: 0;
    }

    input:-webkit-autofill,
    textarea:-webkit-autofill,
    select:-webkit-autofill {
      background: #ffffff;
    }

    .form-line-active {
      background: none;
    }

    /* Redundant text overrides */
    .form-textarea {
      font-family: 'Google font', serif;
      font-weight: 400;
    }

    input,
    textarea {
      font-family: 'Google font', serif;
      font-weight: 400;
      font-size: 14px;
      border: 1px solid #aaaaaa !important;
    }

    .form-input .form-error-message,
    .form-input-wide .form-error-message,
    .form-button-error {
      font-family: 'Google font', serif;
      font-weight: 400;
    }

    label {
      font-family: 'Google font', serif;
      font-size: 14px;
      font-weight: 400;
      color: #000000;
    }

    .form-submit-button,
    .form-submit-reset,
    .form-submit-print,
    .form-screen-button {
      padding: 10px;
      width: 100%;
      font-family: 'Google font', sans-serif;
      font-weight: 600;
      background: #000000;
      color: #fff;
      font-size: 16px;
      border: 1px solid #aaaaaa;
    }
