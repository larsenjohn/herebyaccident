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

## Link JS to specific page content

These next few snippets use the **drupal core** functions and should print in the head, even though it's marked up in the content editor in the admin section.

For external JS libraries. (Mind the 'external')

	<?php
	drupal_add_js ('https://link-to-external.js', 'external');
	?>
        
For inline JS functions. (Mind the 'inline')

	<?php
	drupal_add_js ('Whatever.init(function(){ Whatever.clearFieldOnHide="disable";	Whatever.onSubmissionError="jumpToFirstError"; });', 'inline');
	?>
    
***

## Link CSS to specific page content 

	<?php
	drupal_add_css ('https://link-to-external.css');
	?>

## Inject Custom CSS without altering the theme

This **module** called the [**CSS Injector**](https://www.drupal.org/project/css_injector) seems to do the trick. 
        

