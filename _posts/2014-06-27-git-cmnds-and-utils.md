---
layout: post
date: 2014-06-27
title: Git - personal - cheat sheet
categories: tech
---

## Hosting a git repo

* `git daemon --base-path=. --export-all --reuseaddr --informative-errors --verbose`

## Adding a remote

* `git remote add <remotename> git://127.0.0.1/project_name`

## After that
    * git fetch <remotename>
    * get pull <remotename> <branch name in the remote>
