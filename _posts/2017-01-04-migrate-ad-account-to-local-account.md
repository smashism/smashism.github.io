---
layout: post
title: An Addition to Rich's Account Migration Script
cover: cover.jpg
date:   2017-01-04 14:51:00
categories: posts
---

As I continue to find ways to make moving our Macs off of AD as easily as possible, I found myself turning to Rich's [MigrateADMobileAccounttoLocalAccouint](https://github.com/rtrouton/rtrouton_scripts/tree/master/rtrouton_scripts/migrate_ad_mobile_account_to_local_account) script to see if it would work in our environment. And it does, sweet! But part of what makes a move like this feasible for our organization is making sure something like [NoMAD](http://nomad.menu) is in place for password sync and expiration feedback.

So I made a [small update](https://github.com/smashism/casper-scripts/blob/master/migrate_ad_account_to_local_account.sh) to Rich's script, which once the `Finished` option is selected will 1) install NoMad via a JSS policy on a custom trigger, 2) run recon silently to update Smart Group membership, 3) `sleep 20` to make sure the JSS sees the Smart Group change and apply a configuration profile for the app, and 4) open NoMAD.

My addition looks something like this:

```
# Installing newest version of NoMAD
echo "Installing NoMAD..."
jamf policy -trigger update_nomad >/dev/null # the >/dev/null supresses output of the policy, just to keep things tidy

# Run recon to detect NoMAD and apply configuration settings
echo "Running recon..."
jamf recon >/dev/null # the >/dev/null supresses output of the recon, just to keep things tidy

# Give the JSS a chance to apply the configuration settings
echo "Applying NoMAD settings..."
sleep 10

# Get current user and OS information.
CURRENT_USER=$(/usr/bin/stat -f%Su /dev/console)
USER_ID=$(id -u "$CURRENT_USER")
OS_MAJOR=$(/usr/bin/sw_vers -productVersion | awk -F . '{print $1}')
OS_MINOR=$(/usr/bin/sw_vers -productVersion | awk -F . '{print $2}')

# Launch NoMAD using launchctl.
echo "Launching NoMAD..."
if [[ "$OS_MAJOR" -eq 10 && "$OS_MINOR" -le 9 ]]; then
	LOGINWINDOW_PID=$(pgrep -x -u "$USER_ID" loginwindow)
	launchctl bsexec "$LOGINWINDOW_PID" open "/Applications/NoMAD.app"
elif [[ "$OS_MAJOR" -eq 10 && "$OS_MINOR" -gt 9 ]]; then
	launchctl asuser "$USER_ID" open "/Applications/NoMAD.app"
else
	echo "[ERROR] macOS $OS_MAJOR.$OS_MINOR is not supported."
	exit 1004
fi
exit 0``

You'd want to change the custom trigger to install NoMAD to whatever you prefer.
