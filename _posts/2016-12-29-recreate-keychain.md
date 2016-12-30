---
layout: post
title: Recreating the login keychain via Self Service
cover: cover.jpg
date:   2016-12-29
categories: posts
---

## recreate_keychain.sh

Today I built a new script to run with a Self Service policy that allows a user to recreate their login keychain. The script deletes their old keychain and creates a new one. jamfHelper and AppleScript prompts facilitate warning the user of upcoming prompts, as well as capturing and passing the user's password through while creating the new keychain.

You can see the script (here)[https://github.com/smashism/casper-scripts/blob/master/self-service/recreate_loginkeychain] and read by blogpost about how it all works [here](https://goo.gl/QzluF()
