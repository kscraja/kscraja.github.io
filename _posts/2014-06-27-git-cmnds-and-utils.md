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

#### After that
    * git fetch <remotename>
    * get pull <remotename> <branch name in the remote>

## Setup A Local gitignore without messing up the project config

* <http://vinitkumar.me/gcode/2014/02/14/setup-a-local-gitignore-without-messing-up-project.html>

* Some IDE and Editors create some files which are very specific developer’s environment.
* They need to be ignored by git.
* But we cannot patch .gitignore. It will effect the entire dev team
* Here is the trick..
* go to: cd .git/info/

    There should be a file called exclude.
    Fill it up with the files and directories you want it to ignore
    such as 

    * *.swp, 
    * ~*


