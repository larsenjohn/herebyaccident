---
layout: post
category: post
title: Dante's Squarespace
published: true
---

# Dante's Squarespace #

So, your client wants a custom Squarespace site. Who boy. OK - where to begin.

You can [read all about it here](https://developers.squarespace.com/quick-start), and I'm sure you will over and over as there is extremely little to go on. If you actually found this from the intertubes - good luck - as this is all conjecture.

<hr class="rule">
***

## Circle one - setup ##

This is a git deploy, so this circle is actually quite a mild climate. Pleasant weather actually.

In order to get at it though, you need to "Enable the Developer Mode". This will relinquish it from it's cold crypt.

*Out of the mouths of babes*

> Now that you've chosen your starting point, you need to enable Developer Mode in the site where you are working. In the Site Manager, navigate to Settings -> Advanced -> Developer Mode. At the top right corner of the settings panel, there is a toggle that is set to off. Click the toggle to turn on Developer Mode.

I just started with one of their templates to see how much this will effect my mental health in the future. But - what they don't mention in the quickstart immediately is that it's a colossal pain in the ass to see your changes. So you will need to download the squarespace server from NPM.

```
$ npm install -g @squarespace/server
```

Then cd into where your repo is. It will most likely have a folder name "template". Then you will have to do a special special since you aren't just going to pay them right away, so you have to flag your server with `--auth`.

```
$ squarespace-server https://site-name.squarespace.com --auth
```

At this point, you can just basically hack the thing open and push it. Which is nice. But also super duper not nice is all the commits **go live out of the gate**. So branch like a mofo or find some other way to develop if you ever have one of these fuckers living in the wild.


<hr class="rule">
***

## Circle two - "templating" ##

You will be spending a bit of time scratching your head at the JSON "template.conf". But I'll visit you from the future and tell you that this is important.

*template.conf*

```
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
```

Now just put your.css in the "styles" folder and you are off and running.

***
***

### JS ###

The JS should all be put in the "scripts" folder in the directory. It also looks like it can compile and minify it just to make your life a whole lot worse when you want to debug. But - if you are an actual developer this is handy. Flag it with combo="true" to fuck up the next person you hand this off to.

```
// Plug me into a template part to combine
<squarespace:script src="shitty.js" combo="true" />

// What the Gods command for External libs
<script src="//code.jquery.com/jquery-2.2.1.min.js"></script>
<script>
    window.jQuery || document.write('<script src="scripts/jquery-2.2.1.min.js"><\/script>')
</script>
```

***
***

## site.region ##

Most of the templates have pretty much everything nailed down the "site.region" file. Which I might add has an annoying feature of confusing atom - so I'll have to figure that out... But, nevertheless you will be in here crying in your soup. Yet, I have some good news from the tunnels as I suspect you will be using this...

***
***

## Open block field ##

What does this all mean? I can't tell you that, but one brute force way to "template" is to drop one of these bastards right in the middle. The "open block" field pretty much gives you the basics and can be edited right away.

```
// Mind the id cowboy

<squarespace:block-field id="blockField1" columns="12"/>

```

***
***

### Working with regions ###

You can also come up with [your own custom layouts](https://developers.squarespace.com/layouts-regions/) by creating "regions". It's similar to using includes, but you will need to gang them together differently. First you will need to chop up your layout into various parts, for instance "header.region, "body.region", "footer.region".

Then go into the **template.conf** and string your template under the layouts. Just include all of the regions you want to deal with between the [] brackets.

```
  "name": "...",
  "author": "...",
  "layouts": {
      // the layout that came out of the box
      "default": {
      "name": "Default",
      "regions": ["site"]
    },
      // your cool layout that the designer will balk at
      "custom" : {
      "name" : "Custom",
      "regions" : [ "header", "body", "footer" ]
    }
},
```

***
***

## Fuck the user ##

Now we are cooking with gas - you can bypass the whole shebang and make a custom page if you choose. But they say the user cannot edit with this method - which pretty much makes SP an expensive static host. To make the leap start by making a "pages" folder if there isn't one there already. Then make a couple of files.

Uno - custom.page  
Duo - custom.page.conf  

You don't have to put anything in the .conf for now, but I have seen this snippet. Too bad this doesn't work either, but put it in so people *think* they have the feature. If you just *believe* it's true it most certainly is - Just ask the president.

```
{
  "supportsVideoBackgrounds": true
}
```

So now you can plug in whatever horrible HTML you like in the custom.page file. I have even dropped an open block in there - which SP says you **really can't do**. We will just have to wait I guess.

<hr class="rule">
***
