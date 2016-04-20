---
layout: post
title: Simple XML sitemap
---

# Simple XML sitemap

Still working on this one, so don't take it too seriously. Typically this is needed for large sites or stuff that isn't linked properly. Still, they say it's good for newer sites. So it's worth sending up the flagpole.

A bit about protocol [here](http://www.sitemaps.org/protocol.html) and submitting to Google [here](https://support.google.com/sites/answer/100283?hl=en).

***
<hr class="rule">

## XML from scratch

There are some paid for services and plugins, but for a smaller site you can roll your own.

Basic sample from siteground:

    <?xml version="1.0" encoding="UTF-8"?>
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

      <url>
        <loc>http://www.domain.com/</loc>
          <lastmod>2008-01-01</lastmod>
          <changefreq>weekly</changefreq>
          <priority>0.8</priority>
      </url>

      <url>
        <loc>http://www.domain.com/catalog?item=vacation_hawaii</loc>
          <changefreq>weekly</changefreq>
      </url>

      <url>
        <loc>http://www.domain.com/catalog?item=vacation_new_zealand</loc>
          <lastmod>2008-12-23</lastmod>
          <changefreq>weekly</changefreq>
      </url>

      <url>
        <loc>http://www.domain.com/catalog?item=vacation_newfoundland</loc>
          <lastmod>2008-12-23T18:00:15+00:00</lastmod>
          <priority>0.3</priority>
      </url>

      <url>
        <loc>http://www.domain.com/catalog?item=vacation_usa</loc>
          <lastmod>2008-11-23</lastmod>
      </url>

    </urlset>

From Google:

    <?xml version="1.0" encoding="UTF-8"?>
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
      xmlns:image="http://www.google.com/schemas/sitemap-image/1.1"
      xmlns:video="http://www.google.com/schemas/sitemap-video/1.1">

      <url>
        <loc>http://www.example.com/foo.html</loc>

        <image:image>
           <image:loc>http://example.com/image.jpg</image:loc>
           <image:caption>Dogs playing poker</image:caption>
        </image:image>

        <video:video>
          <video:content_loc>
            http://www.example.com/video123.flv
          </video:content_loc>
          <video:player_loc allow_embed="yes" autoplay="ap=1">
            http://www.example.com/videoplayer.swf?video=123
          </video:player_loc>
          <video:thumbnail_loc>
            http://www.example.com/thumbs/123.jpg
          </video:thumbnail_loc>
          <video:title>Grilling steaks for summer</video:title>  
          <video:description>
            Cook the perfect steak every time.
          </video:description>
        </video:video>
      </url>

    </urlset>

## About the attributes

`<lastmod>`, `<changefreq>` and `<priority>` are optional. Look to the Google example for images and media for a higher level focus.

***

### lastmod

The date of last modification of the file. This date should be in W3C Datetime format. This format allows you to omit the time portion, if desired, and use YYYY-MM-DD.


### changefreq

How frequently the page is likely to change. This value provides general information to search engines and may not correlate exactly to how often they crawl the page. Valid values are:

+ always
+ hourly
+ daily
+ weekly
+ monthly
+ yearly
+ never

The value "always" should be used to describe documents that change each time they are accessed. The value "never" should be used to describe archived URLs.

The value of this tag is considered a hint and not a command. Crawlers may periodically crawl pages marked "never". Use a `<meta name="robots" content="index, follow">` instead of "never" for strict purposes.

### priority

The priority of this URL relative to other URLs on your site. Valid values range from 0.0 to 1.0. This lets the search engines know which pages you deem most important for the crawlers.

Priority scale from top to bottom:

+ 1.0
+ 0.9
+ 0.8
+ 0.7
+ 0.6
+ 0.5 *(default)*
+ ...
+ 0.0

The priority you assign to a page is not likely to influence the position of your URLs in a search engine's result pages. Search engines may use this information when selecting between URLs on the same site.

Also, note that assigning a high priority to all of the URLs on your site is not likely to help.

***
<hr class="rule">

## Straight url XML

    <?xml version="1.0" encoding="UTF-8"?>
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">

      <url>
        <loc>http://fucktheweb.com/</loc>
          <priority>1.0</priority>
      </url>

      <url>
        <loc>http://fucktheweb.com/contact.html</loc>
          <priority>0.9</priority>
      </url>

      <url>
        <loc>http://fucktheweb.com/faq.html</loc>
          <priority>0.8</priority>
      </url>

      <url>
        <loc>http://fucktheweb.com/some-page.html</loc>
      </url>

    </urlset>

***
<hr class="rule">

## Create a robots.txt file

After your sitemap is built you need to show Google where it is. Drop this `robots.txt` file in the root to show the path.

    Sitemap: http://fucktheweb.com/sitemap.xml

## Submit the sitemap

Log into the webmaster tools console and navigate to your domain.

1. **Navigate to:** Crawler
2. **Navigate to:** sitemaps
3. **Select:** Add/Test Sitemaps

Run through the "robots.txt" and "Fetch as Google" tools to verify that the sitemap has been submitted properly.
