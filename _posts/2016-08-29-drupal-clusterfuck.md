---
layout: post
category: post
title: Drupal clusterfuck
published: true
---

# Don't read this if you actually know Drupal #

This is basically a tear stained document of trying to figure out Drupal in a few hours. Feel free to print this, cry on it, then upload to smugmug to reflect on your life.

Also, none of this may *actually* work.

<hr class="rule">
***

## Allow php formatting to a content ##

Go to **Modules** and check off **PHP filter**. Edit your content and select **Text format: PHP code**. Most of the crap that follows this will be in **php code** to leverage the Drupal core functions. 

***

## Add js to specific page content

On your page for external libraries. This should print in the head.

		<?php
		drupal_add_js ('https://link-to-external.js', 'external');
		?>
