---
title: "Github pages, custom domains and Cloudflare"
description: "Github pages, custom domains and Cloudflare"
date: 2026-01-20
tags: [software,Hugo,Gitgub]
categories: [howtos]
---

The steps to getting this on https://linux.plumocelot.uk as oppposed to the github page url badgergeddon.github.io:

1. Set things up on Cloudflare with a CNAME reference linux.plumocelot.uk and point it to badgergeddon.github.io
2. Select "DNS only" and not proxied for setting up otherwise ssl (https) will not work on github pages setup later.
3. Go to your github pages repository and select settings>pages
4.  Enter your custom domain, e.g. mine  was "linux.plumocelot.uk"
5. Save and hopefully your domain will resolve.
6. You should now be able to "Enforce HTTPS"
7. If using a github action to build and deploy (I am using Hugo here) then you need to edit your hugo.toml file in your repo to change the base domain:
eg, mine was: baseurl = "https://linux.plumocelot.uk"
8. Run "Deploy Hugo site to Pages" workflow
9. Enjoy your cheapskate website on your custom domain.