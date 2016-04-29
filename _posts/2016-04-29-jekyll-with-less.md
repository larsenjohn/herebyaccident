---
layout: post
title: Jekyll + LESS
---

# Jekyll + LESS

I'm late to the compiler game. Generally speaking, you can pry the vanilla from my cold dead hands. I'm always afraid some tool on another tool will break and all I want to do is change a couple of styles. I have *no idea* where all of these gem installs go.

Either way, you can't stay stagnant on the internets, so here we go with adding LESS support to jekyll. See you in the forums when I'm crying at my desk.

***
<hr class="rule">

## Install LESS

Easiest is using npm, which is probably dangerous.

    npm install -g less

## Install the gem

It took me a couple of tries here. There is a link ref [here](https://rubygems.org/gems/jekyll-less/versions/0.0.4), and another repo [here](https://github.com/zroger/jekyll-less). In either case you do this:

    gem install jekyll-less

## Add the gem to the config.yml

    gems: ['jekyll-less']

***
<hr class="rule">

## Wonk?

In both instances this borked out on me and I needed to install *another* gemfile called [**therubyracer**](https://rubygems.org/gems/therubyracer/versions/0.12.2).

    gem install therubyracer

After that, running `jekyll build` and `jekyll serve` started the magic.

***
