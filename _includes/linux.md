### Linux

#### Ubuntu

 * Doesn’t support OS level captive portal login in available LTS (long term support) releases so far. Now there is a discussion in Ubuntu WiKi networking section where it is proposed to provide OS level support in coming releases. GNOME (GNU Network Object Model Environment) had introduced automatic login prompt for Wi-Fi captive portals (Wi-Fi access points which required web based login, such as those found in public places) quite a while ago. However this functionality is still unavailable in Ubuntu GNOME, The same is part of wish-list in upcoming Ubuntu LTS releases.

#### Linux (Firefox Browser Installed)

 * Firefox introduces automatic detection of Captive portals and notifies user about the need to log in. Additionally, after Firefox detects a Captive portal, it replaces certificate error pages with a message encouraging user to log in.

 * Firefox determines the existence of a captive portal constraint by attempting to download the file success.txt from http://detectportal.firefox.com/success.txt (there is only one word in that file, the word "success". If it can successfully retrieve that file, it can assume that it is not constrained by a Captive portal. Otherwise, it will trigger an in-browser notification.

#### Linux (Chrome Browser Installed)

 * Chrome introduces automatic detection of Captive portals and notifies user about the need to log in. Additionally, after Chrome detects a Captive portal, it replaces certificate error pages with a message encouraging user to log in.
