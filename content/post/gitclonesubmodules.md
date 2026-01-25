---
title: "Missing Git Submodules?"
description: "Git Submodules"
date: 2026-01-25
tags: [git,submodules,howto]
categories: [software]
---

Here’s something I stumble over almost every time I clone a git repository with submodules.

Those darn folders are empty and using the project fails. Here are two ways to fix that:

## Clone With The Recursive Flag

When issuing your git clone, add a `--recursive` flag. It will look like this:

```
$ git clone git@github.com:user/project.git --recursive
```

And as easy as that, your submodules are there.

If you cloned your repo and don’t mind starting over - delete the freshly cloned repository and add that `--recursive` to the command.

If you don’t want to start over…

## Fix Those Submodules With An Init

You can fix your submodules in hindight, with this command:

```
$ git submodule update --init
```

This will fill in those missing pieces and you’ll be able to finally get back to interacting with your git project - submodules and all.

As I’m writing this, I’m considering to add `--recursive` by default when cloning something in the future. This way, I’ll never stumble over broken submodules again.