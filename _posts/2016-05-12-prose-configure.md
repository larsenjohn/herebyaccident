---
layout: post
category: post
published: true
title: Prose configure
---
# Prose.io configure

This is a test. Tricky to configure for dummies like me.

***
<hr class="rule">

I want to cut the draft feature and go cowboy. Nobody's looking anyway.

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
