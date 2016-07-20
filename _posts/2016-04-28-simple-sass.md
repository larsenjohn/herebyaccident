---
layout: post
category: post
title: Basic SASS
published: true
---

# Simple SASS

So, I'm late to the complier game. Generally speaking, you can pry the vanilla from my cold dead hands. But that's neither here nor there since in the interwebs you can't stay stagnant for too long.

Since [jekyll](https://jekyllrb.com/) is [SASS](http://sass-lang.com/guide) ready right out of the box, it fits my lazy edginess.

***
<hr class="rule">

I needed to choose my own adventure. In this case it's SCSS. Probably a mistake.

## Indenting

Probably the easiest way to start, and one of the most intuative aspects of SASS is you can indent *any* of your styles just like media queries which is really handy. Like so:

	#new-id {
      .some-class {
        text-align: center;
      }
        
      .another-class {
        display: block;
      }
    }
    
Processes to:

	#new-id .some-class {
      text-align: center;
    }
    
    #new-id .another-class {
      display: block;
    }


## Variables

Think of variables as a way to store information that you want to reuse throughout your stylesheet. You can store things like colors, font stacks, or any CSS value you think you'll want to reuse. Sass uses the $ symbol to make something a variable.

    $font-stack: "Helvetica", sans-serif;
    $primary-color: #333;


    body {
      font: $font-stack;
      color: $primary-color;
    }

Processes to:

    body {
      font: "Helvetica", sans-serif;
      color: #333;
    }

## Mixins

A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes.

    @mixin border-radius($radius) {
      -webkit-border-radius: $radius;
      -moz-border-radius: $radius;
      -o-border-radius: $radius;
      border-radius: $radius;
    }

    .box {
      @include border-radius(10px);
    }

Processes to:

    .box {
      -webkit-border-radius: 10px;
      -moz-border-radius: 10px;
      -o-border-radius: 10px;
      border-radius: 10px;
    }

## Extend/Inheritance

Using `@extend` lets you share a set of CSS properties from one selector to another. This example creates a simple series of messaging for errors, warnings and successes.

    .message {
      border: 1px solid #ccc;
      padding: 10px;
      color: #333;
    }

    .success {
      @extend .message;
      border-color: green;
    }

    .error {
      @extend .message;
      border-color: red;
    }

    .warning {
      @extend .message;
      border-color: yellow;
    }

Processes to:

    .message, .success, .error, .warning {
      border: 1px solid #cccccc;
      padding: 10px;
      color: #333;
    }

    .success {
      border-color: green;
    }

    .error {
      border-color: red;
    }

    .warning {
      border-color: yellow;
    }

***
<hr class="rule">

## Common snippets

Sure, you may say "why don't you just recompile bootstrap (or some other library everyone now hates) instead of overriding it? Isn't that just a hack?"

Yes, yes it is.

***

## Common mixins

Square up

    @mixin no-radius {
      border-radius: 0;
      -webkit-border-radius: 0;
      -moz-border-radius: 0;
      -o-border-radius: 0;
    }

    @mixin no-text-shadow {
      text-shadow: none;
      -webkit-text-shadow: none;
      -moz-text-shadow: none;
      -o-text-shadow: none;
    }

    @mixin no-box-shadow {
      box-shadow: none;
      -webkit-box-shadow: none;
      -moz-shadow: none;
      -o-box-shadow: none;
    }

    .flat {
      @include no-radius;
      @include no-text-shadow;
      @include no-box-shadow;
    }


Border radius

    @mixin border-radius($radius) {
      border-radius: $radius;
      -webkit-border-radius: $radius;
      -moz-border-radius: $radius;
      -o-border-radius: $radius;
    }

    .box {
      @include border-radius(4px);
    }

Text shadow

    @mixin text-shadow($shadow) {
      text-shadow: $shadow;
      -webkit-text-shadow: $shadow;
      -moz-text-shadow: $shadow;
      -o-text-shadow: $shadow;
    }

    p.drop-text {
      @include text-shadow(0 0 5px #000);
    }

Box shadow

    @mixin box-shadow($shadow) {
      box-shadow: $shadow;
      -webkit-box-shadow: $shadow;
      -moz-box-shadow: $shadow;
      -o-box-shadow: $shadow;
    }

    .inset-box {
      @include box-shadow(5px 5px 5px inset #000);
    }

Opacity

    @mixin opacity($opacity) {
      opacity: $opacity;
      -moz-opacity: $opacity;
      -webkit-opacity: $opacity;
      -o-opacity: $opacity;
      $opacity-ie: $opacity * 100;
      filter: alpha(opacity=$opacity-ie); //IE8
    }

    img:hover {
      @include opacity(0.8);
    }

Simple CSS3 global ease transition

    @mixin ease {
      transition: all 0.15s ease-in-out;
      -webkit-transition: all 0.15s ease-in-out;
      -moz-transition: all 0.15s ease-in-out;
      -o-transition: all 0.15s ease-in-out;
    }

    a {
      @include ease;
    }

Margin 0 auto

    @mixin auto {
      display: block;
      margin: 0 auto;
    }

    .img-block {
      @include auto;
    }

Basic gradients

    @mixin gradient($start-color, $end-color) {
        background-color: $start-color;
        background-image: -webkit-gradient(linear, left top, left bottom, from($start-color), to($end-color));
        background-image: -webkit-linear-gradient(top, $start-color, $end-color);
        background-image: -moz-linear-gradient(top, $start-color, $end-color);
        background-image: -ms-linear-gradient(top, $start-color, $end-color);
        background-image: -o-linear-gradient(top, $start-color, $end-color);
        background-image:linear-gradient(top, $start-color, $end-color);
        filter: progid:DXImageTransform.Microsoft.gradient(start-colorStr='#{$start-color}', end-colorStr='#{$end-color}');
    }

    @mixin linear($start-color, $end-color) {
        background-color: $start-color;
        background-image: -webkit-gradient(linear, left top, right top, from($start-color), to($end-color));
        background-image: -webkit-linear-gradient(left, $start-color, $end-color);
        background-image: -moz-linear-gradient(left, $start-color, $end-color);
        background-image: -ms-linear-gradient(left, $start-color, $end-color);
        background-image: -o-linear-gradient(left, $start-color, $end-color);
        background-image: linear-gradient(left, $start-color, $end-color);
        filter: progid:DXImageTransform.Microsoft.gradient(start-colorStr='#{$start-color}', end-colorStr='#{$end-color}', gradientType='1');
    }

    .top-gradient {
      @include gradient(#aaa, #000);
    }

    .left-gradient {
      @include linear(#aaa, #000);
    }

***

## Common variables

In case you are combining families

    $serif: "Branded Serif Font", serif;
    $sans: "Branded Sans Serif Font", sans-serif;

    body {
      font-family: $sans-serif;
    }

    h1, h2 {
      font-family: $serif;
    }
