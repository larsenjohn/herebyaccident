---
layout: post
category: post
title: AWS S3 resource sharing
published: true
---

# Swinging shit through AWS S3

I know all of you are laughing since you have been able to do this since, like Y2K or something. But not me. Since I really don't like anything, I probably won't like this - and drop it later once I get a bill for like a million dollars.

***
<hr class="rule">

## Cat pictures

Sure, I guess you can just make a bucket and just open it up to the world. But the higher ups at Amazon says it's a [no-no](https://aws.amazon.com/articles/5050). So, one way to do it is to spin up a "website" and serve your stuff from a public folder.

See the utterly inspiring post [here](http://herebyaccident.com/post/2016/04/05/aws-s3.html) about it. I just work up a whatever.com and use the S3 endpoint once it's all up to speed. You will have to go through the trouble of making a dummy index.html and 404.html page. I know you are lazy, so here is the bucket policy once again.

<pre>
{
  "Version":"2012-10-17",
  "Statement":[{
	"Sid":"PublicReadForGetBucketObjects",
        "Effect":"Allow",
	  "Principal": "*",
      "Action":["s3:GetObject"],
      "Resource":["arn:aws:s3:::fucktheweb.com/*"
      ]
    }
  ]
}
</pre>

Now you can just link out to "https://s3.amazonaws.com/fucktheweb.com/lamepost/super-cat.jpg".

***
<hr class="rule">

## Font wizardry

Not so fast. Apparently AWS is so damn awesome you can't just serve up your souped up comic sans font you stole from napster in the 90's. Firefox gets all jittery about it. So *now* you have to use some BS called CORS. Or to be cool when you are around the big developers it's called "Cross-Origin Resource Sharing."

So jump through the following hoop:

+ Select your "root" bucket
+ Select Properties
+ Select Permissions
+ Select Edit CORS Configuration
+ Check that is says this:

		<?xml version="1.0" encoding="UTF-8"?>
		<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
    		<CORSRule>
        		<AllowedOrigin>*</AllowedOrigin>
        		<AllowedMethod>GET</AllowedMethod>
        		<MaxAgeSeconds>3000</MaxAgeSeconds>
        		<AllowedHeader>Authorization</AllowedHeader>
    		</CORSRule>
		</CORSConfiguration>

Generally, you can use the default for this. For my deal I used the `<AllowedOrigin>*</AllowedOrigin>` or the * setting to use all URL's instead of a specific one.

So, now you should be able to hook up your fonts like so:

<pre>
@font-face {
  font-family: KillerComicSans;
  src: url('https://s3.amazonaws.com/fucktheweb.com/lamepost/fonts/KillerComicSans.eot');
  src: url('https://s3.amazonaws.com/fucktheweb.com/lamepost/fonts/KillerComicSans.eot?#iefix') format('embedded-opentype'),
       url('https://s3.amazonaws.com/fucktheweb.com/lamepost/fonts/KillerComicSans.woff') format('woff'),
       url('https://s3.amazonaws.com/fucktheweb/lamepost/fonts/KillerComicSans.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}

body {
  font-family: 'KillerComicSans', sans-serif;
}
</pre>

***
<hr class="rule">

## CLI Terror 

So there is a CLI tool where you can fuck up your machine. Which I probably already have. So at this point I'm going to just "copy" stuff instead of snycing it. Cause you know, it may remove everything that isn't snyced to S3.

I also suck at paths - so I like to **nav to the folder I want to copy to first**. To copy everything from an s3 bucket you can do this mojo.

Like so:

	aws s3 cp s3://bucket-name . --recursive
