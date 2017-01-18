---
layout: post
title: Getting the logged-in Apple ID
cover: cover.jpg
date:   2017-01-18 14:54
categories: posts
---

macOS Sierra does quite a few things differently with the App Store, including the lack of a `debug` menu option and the lack of a `com.apple.storeagent.plist` which is where folks used to cull that information for reporting purposes.

After asking in the [#jamfnation channel on the MacAdmins Slack](https://macadmins.slack.com/archives/jamfnation) a few of us came up with the following alternative to get that information:

`/usr/libexec/PlistBuddy -c "Print :PrimaryAccount:0:1:identifier" /Users/$username/Library/Preferences/com.apple.commerce.plist`

I created an Extension Attribute out of the above [here](https://github.com/smashism/casper-extension-attributes/blob/master/appestore_appleid.sh). Detailed blog post forthcoming.
