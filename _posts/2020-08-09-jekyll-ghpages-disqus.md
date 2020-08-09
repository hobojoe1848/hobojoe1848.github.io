---
title: "How to Configure Disqus Comments on a Github Pages Jekyll Blog"
date: 2020-08-09T12:27:00+1000
author: Julian
layout: post
comments: True
permalink: jekyll-ghpages-disqus
author: Julian
description: "A simple reminder for myself on how to configure Disqus comments on a Jekyll based GitHub pages blog"
categories:
 - Technology
 - Guide
 - Blogging
tags:
 - tech
 - blogging
 - GitHub pages
 - jekyll
 - disqus
image: ""
---

This is a simple reminder for myself on how to configure Disqus comments on a Jekyll based GitHub pages blog. Why? Because like my previous post on getting the HTTPS certificate going, this just isn't clearly detailed in one place.

## The Confusion

Naturally, I went to Google to find the answer and stumbled across a boat load of blogs and StackOverflow articles detailing how to get Disqus up and running on a Jekyll blog.

There were all sorts of posts on inserting tags, code and HTML into your default template to get it operational. Then there came the posts on authenticating to your Disqus account and so on.

What a waste of time! I spent at least an hour digging around my Jekyll GitHub Pages templates looking for the right place to put this stuff. The confusion was further compounded by finding there was already some Disqus code in my default comments template.


## The Solution

Jekyll already comes with the required Disqus code in the `./_includes/comments.html` file! 

Furthermore, the only required configuration setting for Disqus in this file, references a Jekyll entry defined in the base `./_config.yml` file: `disqus_username:`.

No shit, I just appended my Disqus username to `disqus_username` and the Disqus comments for my site loaded on reload.

Absolute BREEZE to set up.


## Conclusion

Definitely cracks me up. I should have just dug around the `comments.html` or `_config.yml` files but I honestly couldn't have imagined that Jekyll would have included settings and template code for a third party plugin like Disqus by default - that's just bloody brilliant.

On the flip side, not being able to find this info anywhere when I Googled it leaves me a bit puzzled.

Either way, it's up and running now so no dramas! Note taken for future reference.

-- Julian
