---
layout: post
title: git cheat sheet
---

# git reference for the feeble

Hoorah, git commands. Another exiting day at the races.

***
<hr class="rule">

## Branching

Checkout a new branch

    git checkout -b branch-name

Delete branch

    git branch -d branch-name

Push branch

    git push origin branch-name

Or alternately the master

    git push origin master

## Updating

Basic update (pull)

    git pull

Merge branch to master

    git merge branch-name

## Logging

Check the history Log

    git log

Get **out of the Log type "q"**.

Drop all local changes and commits, fetch the latest history from the server and point your local master branch at it like this.

    $ git fetch origin
    $ git reset --hard origin/master

***
