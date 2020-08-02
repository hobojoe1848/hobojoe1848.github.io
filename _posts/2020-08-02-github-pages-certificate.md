---
title: "How to Configure a Certificate on a Github Pages Jekyll Blog"
date: 2020-08-02T19:44:00+1000
author: Julian
layout: post
comments: True
permalink: GitHub-pages-certificate
author: Julian
description: "A simple note for myself on getting the HTTPS certificate for my GitHub pages blog"
categories:
 - Technology
 - Guide
 - Blogging
tags:
 - tech
 - blogging
 - GitHub pages
 - jekyll
 - certificate
image: ""
---

A quick note for anyone (myself) that may need help with configuring their certificate for the Jekyll based GitHub Pages blog.

## The Setup

- This is in regards to setting up HTTPS on a Jekyll based GitHub Pages blog. 

- All files are stored in a GitHub repository using the standard format of `GitHub-username.github.io`.

- At the time of writing, my domain `juliansequeira.dev` is registered through Google Domains.


## The Problem

After manually adding the custom A records and CNAME to Google Domains, I added the custom domain `juliansequeira.dev` to the Settings page of my GitHub pages repo.

I naively thought that was all I had to do but as GitHub pages are not a "hosting partner" of Google, the HTTPS certificate that's required for a valid HTTPS connection isn't automatically handled by Google.

As a result, when loading this blog, I would get a "not trusted" message in the browser and was unable to load the site. Not a good look!


## The Solution

Both Google Domains and GitHub Pages recommended I used [Let's Encrypt](https://letsencrypt.org) as the "Certificate Authority" (CA) to issue the certificate for my site.

Of course, the documentation is not in plain English, assumes a shitload and is just overall frustrating for someone who's never had to deal with this before.

The solution was rather minimal for the frustration this all caused:

1. Head to your domain hosting dashboard (Google Domains for me).
2. Go to DNS or wherever you create your custom records (A records, CNAME, etc).
3. Add the following record. Make sure you enter the `Data` section in exactly as written here:
~~~~
Name: <whatever you want>
Type: CAA
TTL: <default> (1h was my default)
Data: 0 issue “letsencrypt.org”
~~~~

4. Click Add or Save or Commit or Apply or whatever.
5. Head to the Settings page of your GitHub pages repo.
6. Under the "Options" menu item, scroll down to the "GitHub Pages" section.
7. Check the "Enforce HTTPS" check box.
8. Now your site should be using the certificate and be HTTPS secure.


## Conclusion

Seriously, it frustrates me how sparse the information to do this was. Why it's not explained in plain English on GitHub pages is beyond me. 

It's almost like they pass the buck to be honest. In their [help pages](https://docs.github.com/en/github/working-with-github-pages/troubleshooting-custom-domains-and-github-pages) on this topic, they mention A and CNAME records but shaft you on the Certificate Authority stuff. All they do is link you to *Let's Encrypt* and dust their hands.

It could also just be that I'm noob at this I guess! Either way, it's working now thus this rough documentation in case I ever need to do this again.

-- Julian
