---
layout: page
date: 2014-06-15
title: Ubuntu, Linux - cmds, utils etc.
categories: tech
---

## Finding the current version of ubuntu
- uname -mrs
- lsb_release -a
- cat /etc/issue

## How to upgrade to latest ubuntu

* sudo apt-get update
* sudo apt-get upgrade
* sudo apt-get dist-upgrade

Then begin the upgrade process


* sudo apt-get install update-manager-core
* sudo do-release-upgrade
    - sudo do-release-upgrade -d (if **No new release found** msg pops up)

* <http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04>
* <http://lawrit.lawr.ucdavis.edu/it-help-center/how-to/upgrading-ubuntu-via-command-line>

## Switching terminals

* Ctrl + Alt + F1....F7
    - F7 - desktop

## Hibernating, Suspend system

* sudo pm-suspend
* sudo pm-hibernate

## Details for processor

* cat /proc/cpuinfo 

## Battery Charge details

* acpi
