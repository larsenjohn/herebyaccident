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




