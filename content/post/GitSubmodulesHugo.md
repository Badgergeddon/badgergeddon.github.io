---
title: Fixing Hugo Gallery and updating a Git Submodule
description: Fixing Hugo Gallery and updating a Git Submodule
date: 2026-02-07
tags: [hugo, git]
categories: [software]
---

```
 # fixing a submodule 
$ git submodule update --remote --merge 

```
I use the Hugo gallery [theme](https://themes.gohugo.io/themes/hugo-theme-gallery/)

It broke on my [britishbogroll](https://gallery.britishbogroll.uk/) gallery which I think is due to an update to sasl which resizes/processes images and an obsolete reference.

After a certain amount of faffing I re-pulled my repo and updated the git submodule - the theme which fixed it. As there are quite lot of pictures you sometimes have to be patient to alow Hugo to rebuild it which is probably how I broke it before.. See the invocation above!