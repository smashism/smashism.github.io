---
layout: post
title: Programmatically unmanaging computers &amp; devices via Jamf Pro API using bearer-auth token authentication.
cover: modern-unmanage.png
date:   2024-04-05 11:05pm
categories: posts
---

#### The gist

With the impending deprecation of basic auth for the Jamf Pro API I took some time to update my computer+device cleanup scripts to use bearer-auth token to do the needful.

The main workflow is largely the same:
1. Run an advanced search for devices (computers or mobile devices)
2. Export a report that includes JSS IDs
3. Copy out the JSS ID column into the array in the appropriate script
4. 🆕 Run script and enter `jamfProURL`, `jssUser`, and `jssPassword` when prompted.

#### The scripts

<script src="https://gist.github.com/smashism/fabfdc4910ff8a8c37594134259da7e4.js"></script>

<script src="https://gist.github.com/smashism/906e47fb760170a28ebb78829656226d.js"></script>

Treat this post as a moment in time; these scripts may be fleeting! 🪽

gl;hf<br />
💖 Em
