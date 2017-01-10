---
layout: post
title: Checking and Enabling FileVault 2
cover: cover.jpg
date:   2017-01-10 17:40:00
categories: posts
---

I spent the better part of Monday trying to make a [simple AppleScript application](http://grahampugh.github.io/2017/01/08/better-application-to-run-shell-scripts-with-admin-rights.html) that could act as an all-in-one Disk Encryption enabler/checker utility.

![Disk Encryption](https://raw.githubusercontent.com/smashism/smashism.github.io/master/images/Screen%20Shot%202017-01-09%20at%202.58.57%20PM.png)

All the AppleScript app does, really, is run a shell script nestled inside. The shell script spits out dialogs with `fdesetup status`, and if the status is something other than `FileVault is On.` it will run a custom trigger for the JSS to run and configure an institutional FileVault 2 policy.

You can see the script [here](https://github.com/smashism/casper-scripts/blob/master/policy_fv2check.sh). Detailed blog post forthcoming.
