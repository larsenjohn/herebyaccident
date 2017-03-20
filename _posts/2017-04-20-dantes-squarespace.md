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

I just started with one of their templates to see how much this will effect my mental health in the future. But - what they don't mention in the quickstart immediately is that it's a colossal pain in the ass to see your changes. So you will need to download the squarespace server from NPM.

    $ npm install -g @squarespace/server

Then cd into where your repo is. It will most likely have a folder name "template". Then you will have to do a special special since you aren't just going to pay them right away, so you have to flag your server with "--auth".

    $ squarespace-server --auth https://site-name.squarespace.com --auth

At this point, you can just basically hack the thing open and push it. Which is nice. But also super duper not nice is all the commits **go live out of the gate**. So branch like a mofo or find some other way to develop if you ever have one of these fuckers living in the wild.


***
***

## Circle two - "templating" ##

You will be spending a bit of time scratching your head at the JSON "template.conf". But I'll visit you from the future and tell you that this is important.

*template.conf*

    "stylesheets": [
      "sometemplate.less",
      "sometemplate.less",
      "sometemplate.less",
      "sometemplate.less",
      "sometemplate.less",
      "sometemplate.less",
      // add your css here asshole
      "your.css"
    ],

Now just put your.css in the "styles" folder and you are off and running.
