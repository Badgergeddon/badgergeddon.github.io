---
title: "Docker Cheat Sheet"
description: "Docker Cheat Sheet"
date: 2026-01-25
tags: [howto,docker]
categories: [software]
---

Docker Cheatsheet:

``` 
# pull/update an image
$ docker pull ghcr.io/shaarli/shaarli:release
# run a container from an image
$ docker run ghcr.io/shaarli/shaarli:latest
# list available images
$ docker images ls
# list running containers
$ docker ps
# list running AND stopped containers
$ docker ps -a
# run a command in a running container
$ docker exec -ti <container-name-or-first-letters-of-id> bash
# follow logs of a running container
$ docker logs -f <container-name-or-first-letters-of-id>
# delete unused images to free up disk space
$ docker system prune --images
# delete unused volumes to free up disk space (CAUTION all data in unused volumes will be lost)
$ docker system prune --volumes
# delete unused containers
$ docker system prune
```