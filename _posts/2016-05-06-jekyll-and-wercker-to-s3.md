---
layout: post
title: Using Wercker to deploy to S3
---

# Deploy a Jekyll site to S3 using Wercker

In my efforts to make my life infinitely more complicated, there is this mess. I'm not sure when FTP became a dirty word, maybe it's when the "S" got involved and things just went off the rails.

Anyway, here is a way to make a one page site stupidly verbose.

Before you will be able to deploy you will need to setup a `wercker.yml` file and sync it to your account. You will also need to set your AWS SSH keys and bucket urls through your wercker account, thus keeping them secret so you can safely use git to track your `wercker.yml` in the root of your repo.

***
<hr class="rule">

### Box

In this case it's ruby, so the scripts will be similar to OSX terminal. There are a bunch available depending on which app you want to deploy.

### Install dependencies

Using the build step this will do the following:

**build:**

* Run a bundle-install and verify everything is up to date
* Run script to build the site, effectively compiling the files to the `_site` folder.

**deploy**

* s3sync to AWS
* Check AWS keys
* Check AWS target bucket
* Source_dir: `_site` folder path

***

wercker.yml

    box: wercker/ruby
    build:
    steps:
      - bundle-install
      - script:
          name: generate site
          code: bundle exec jekyll build --trace
    deploy:
    steps:
        - s3sync:
            key_id: $KEY
            key_secret: $SECRET
            bucket_url: $URL
            source_dir: _site/
            opts: |
                --add-header Cache-Control:max-age=60
                --no-preserve
