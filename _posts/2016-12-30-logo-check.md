---
layout: post
title: Logo Check
cover: cover.jpg
date:   2016-12-30 12:40:00
categories: posts
---

## Checking for a Company Logo

Hey y'all. I found myself using a company logo quite a bit in jamfHelper and AppleScript prompts during policies, so I though it would be handy to have a script with logic to check and see if an icon is present and installing on demand, rather than including a .pkg installer in every policy that requires it. 

It's a relatively simple script, which you can see [here](https://github.com/smashism/casper-scripts/blob/master/policy_CompanyLogo.sh). Replace the `/path/to/CompanyLogo.icns` with wherever the logo is you want to check for. Echos are included so that the policy logs show if the icon needed to be installed or not. This script could be easily updated to check for all sorts of things and install other things as needed.

In the JSS you need two policies:
1. Whatever policy you are running that includes a script with jamfHelper pop-ups, etc., with the policy_CompanyLogo.sh also included set to run `Before` other installers/scripts.
2. A second policy that runs on the custom trigger you specify in the policy_CompanyLogo.sh.

I got the idea for this from both my [NoMAD update script](https://github.com/smashism/casper-scripts/blob/master/update_nomad.sh) and Rich Trouton's [printer driver check script](https://gist.github.com/rtrouton/8830790#file-gistfile1-sh).

As always, test before deploying in production!
