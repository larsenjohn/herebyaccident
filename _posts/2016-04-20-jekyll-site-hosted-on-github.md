---
layout: post
title: Github pages hosting
---

# Host a Jekyll site on Github

This is a super condensed version of [these docs](https://help.github.com/articles/creating-project-pages-manually/). All things below are referencing a site already manually set up for jekyll development. You can also just use the **automatic generator** for simple startup projects.

***
<hr class="rule">

## Make a fresh repository

Create a fresh repository and clone it.

    git clone .../repo-name


## Create a gh-pages branch

Create a new gh-pages branch.

    $ cd fresh-clone
    $ git checkout --orphan gh-pages

Now empty out the folder in the new branch.

## Add content and push

Drop your files into the repo, add, commit and push the origin to github.

    $ git add -A
    $ git commit -m "first gh-pages commit"
    $ git push origin gh-pages

## Check your github.io url

You can check the public url by going to http://yourgithubaccount.github.io/repo-name to see if it stuck. Github pages kind of has a lag sometimes so it can take a few.

***
<hr class="rule">

## Configure the DNS

Go to the new repository on github and create a **new file**. Title it **CNAME** and drop the domain name in it. This should be **done first** before changing any settings at the domain host.

    fucktheweb.com

In this case the canonical name will be fucktheweb.com. You can also use *www.fucktheweb.com* if necessary, but the records will need reflect that through the domain registrar.

***

## Change the DNS at the registrar

1. Create one **A record** *(@)* for: 192.30.252.153
2. Create one **A record** *(@)* for: 192.30.252.154
3. Create one www **CNAME record** for: yourgithubaccount.github.io

The CNAME can also be pointed to your particular repository, for instance yourgithubaccount.github.io/repo-name
