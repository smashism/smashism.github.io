---
layout: post
title: Quickly generate random serial numbers
cover: randomsn.png
date:   2018-09-05 12:45pm
categories: posts
---

At the last Austin Apple Admins meetup I gave a talk about building VMs designed for testing DEP and MDM. Part of what I mentioned was using vfuse to generate random serial numbers with the `-s` flag when using a template to generate a VM. Sometimes it's helpful to be able to quickly generate a random serial number—one that is well-formed and won't break an profile-based enrollment in an MDM—without having to build a whole new VM.

I threw together a function that can be put into a bash profile that is used as an alias to quickly generate a serial number.

<script src="https://gist.github.com/smashism/8068e42ecd3d0374707f0bf583d3ea83.js"></script>

Just throw that in your bash profile (which you can get to by typing `nano .bash_profile` (replace `nano` with your editor of choice) to add the above function as an alias to your profile. Open a new terminal window and you can simply type `randomsn` to have a well-formed serial number generated for you.

gl;hf<br />
💖 Em
