---
layout: post
category: post
published: true
title: Github pages prose.io config
---
# Prose.io config

This is super rough, just getting my head wrapped around all the variables. Most important area for this config is getting the path straight for the front matter template.

***
<hr class="rule">

    prose:
    rooturl: '_posts'
    media: 'media'
    metadata:
    _posts:
      - name: "category"
        field:
          element: "hidden"
          value: "post"
      - name: "layout"
        field:
          element: "hidden"
          value: "post"
      - name: "title"
        field:
          element: "text"
          label: "Title"
          value: ""
    _posts/static:
      - name: "layout"
        field:
          element: "hidden"
          value: "page"
      - name: "title"
        field:
          element: "text"
          label: "Title"
          value: ""
      - name: "permalink"
        field:
          element: "text"
          label: "Permalink"
          value: ""
