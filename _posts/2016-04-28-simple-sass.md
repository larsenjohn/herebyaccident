---
layout: post
title: Basic SCSS
---

# Simple SASS (SCSS)

So, I'm late to the complier game. Generally speaking, you can pry the vanilla from my cold dead hands. But that's neither here nor there since in the interwebs you can't stay stagnant for too long.

Since jekyll is [SASS](http://sass-lang.com/guide) ready right out of the box, it fits my lazy edginess.

***
<hr class="rule">

So, I needed to choose my own adventure. In this case it's SCSS. Probably a mistake.

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
      -ms-border-radius: $radius;
      border-radius: $radius;
    }

    .box {
      @include border-radius(10px);
    }

Processes to:

    .box {
      -webkit-border-radius: 10px;
      -moz-border-radius: 10px;
      -ms-border-radius: 10px;
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
