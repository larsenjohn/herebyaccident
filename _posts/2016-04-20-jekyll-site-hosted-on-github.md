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

    $ cd repo-name
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

Go to the new repository on github and create a **new file**. Title it "**CNAME**" and drop the domain name in it. This should be **done first** before changing any settings at the domain host.

    fucktheweb.com

In this case the canonical name will be fucktheweb.com. You can also use *www.fucktheweb.com* if necessary, but the records will need reflect that through the domain registrar.

***

## Change the DNS at the registrar

1. Create one **A record** *(@)* for: 192.30.252.153
2. Create one **A record** *(@)* for: 192.30.252.154
3. Create one www **CNAME record** for: yourgithubaccount.github.io/repo-name

The CNAME can also be pointed to your particular repository, for instance yourgithubaccount.github.io/repo-name

***
<hr class="rule">

## Using the the github.io domain

The links will bork out unless you utilize the liquid tag {{ "{{ site.baseurl " }}}} throughout. For instance:

    <link href="{{ "{{ site.baseurl " }}}}/css/styles.css" rel="stylesheet">

The baseurl path needs to be defined in the `config.yml` file like so:

    # Site settings
    baseurl: "/repo-name"

This will render the path to the github repository name. For example http://yourgithubaccount.github.io/repo-name.

Ala `<link href="{{ "{{ site.baseurl " }}}}/css/styles.css" rel="stylesheet">` compiles to `<link href="/repo-name/css/styles.css" rel="stylesheet">`.

This will also clear up any links in the dev `jekyll serve` environment. This applies to all linked files like images as well.

    <img class="img-responsive full" src="{{ "{{ site.baseurl " }}}}/images/lame-shit.jpg" alt="baseurl lame shit">

***
