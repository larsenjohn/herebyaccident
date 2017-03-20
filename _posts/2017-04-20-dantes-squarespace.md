---
layout: post
category: post
title: Dante's Squarespace
---

# Dante's Squarespace #

So, your client wants a custom Squarespace site. Who boy. OK - where to begin.

You can [read all about it here](https://developers.squarespace.com/quick-start), and I'm sure you will over and over as there is extremely little to go on.

<hr class="rule">
***

## Circle one - setup ##

This is a git deploy, so this circle is actually quite a mild climate. Pleasant weather actually.

In order to get at it though, you need to "Enable the Developer Mode". This will relinquish it from it's cold crypt.

*Out of the mouthes of babes*

> Now that you've chosen your starting point, you need to enable Developer Mode in the site where you are working. In the Site Manager, navigate to Settings -> Advanced -> Developer Mode. At the top right corner of the settings panel, there is a toggle that is set to off. Click the toggle to turn on Developer Mode.

I just started with one of their templates to see how much this will effect my mental health in the future. But - what they don't mention in the quickstart is that it's a colossal pain in the ass to see your changes. So you will need to download the squarespace server from NPM.

    $ npm install -g @squarespace/server
    $ npm start
