---
layout: post
title: Analytics starter settings
---

# Common Google Analytics settings

Basic checklist to go through before all your analytics reports go off the rails.

***
<hr class="rule">

## Set up filtering

Locate your Property url from the list and navigate to:

1. Admin >
2. Under *View* Section
3. Filters >

### Exclude localhost

1. Add filter
2. **Filter Name:** Localhost
3. **Filter type:** Custom > Exclude
4. **Filter Field:** IP Address
5. **Filter Pattern:** `192\.168\.2\.100` (whatever your IP is)

You will need to use the `\.` between your development IP address like the example.

![Filter localhost](/images/ref/ga-filter-localhost.jpg)

### Eliminate redundant www. (search and replace)

1. Add filter
2. **Filter Name:** Search and replace
3. **Filter Type:** Custom > Search and Replace
4. **Filter Field:** Hostname
5. **Search String:** `^www\.`

![Filter localhost](/images/ref/ga-filter-search-and-replace.jpg)

<hr class="rule">

## Set up an exclusion list

Remove third party services and authors for destination url's.

1. Admin >
2. Under *Property* Section
3. Tracking Info >
4. Referral Exclusion list >
5. **Select:** Add Referral Exclusion

Typical exclusion url: submit.jotformpro.com

![Filter localhost](/images/ref/ga-exclusion-list.jpg)

<hr class="rule">

## Set up goals

This is a basic destination goal. For example, an "order now" or form "submit" verification url.

1. Admin >
2. Under *View* Section
3. Goals >
4. **Select:** New Goal

### Goal Setup:

1. **Select:** Custom

### Goal Description

1. **Name:** *Goal Name*
2. **Type:** Destination

### Goal Details

1. **Destination:** Equals to: /my-destination.html

Save goal and verify that **recording is on**.
