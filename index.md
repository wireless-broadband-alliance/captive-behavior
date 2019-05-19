## Background

Public Wi-Fi networks offering short-term or temporary internet access commonly begin new connections using a Captive Portal Mini-Browser. This also happens in fixed and cellular networks in the case of insufficient balance for prepaid tariff plans. Each platform has a native version that is "baked" into the OS. There are also commercial browsers, like Firefox and Chrome that have this built-in support to detect and navigate to the Captive Portal. This mode uses a web-view pushed to the client and has limited capabilities for branding, advertising and other monetization tactics along with limited capabilities with special authorization processes and paid access.

The aim for this project is to define existing use cases for client devices and client manufacturers. 


## Compatibility Matrix (latest versions only)

| Platform | Connection Method | Default Browser | Details |
| --- | --- |
| iOS | Mini-Browser | Websheet | [More Details](#ios) |
| Android | :white_check_mark: | :x: | [More Details](#google-android) |
| Samsung Android | :white_check_mark: | :x: | [More Details](#samsung-android) |
| MacOS | :white_check_mark: | :x: | [More Details](#macos) |
| Windows 10 | :white_check_mark: | :x: | [More Details](#windows10) |



## Contents

- [Existing Device Behavior](#existing)
  - [All](#all)
    - [Mobile](#mobile)
      - [Apple](#apple)
        - [iOS](#ios)
        - [iOS 11+](#ios11)
        - [iOS 6+](#ios6)
      - [Android](#android)
        - [9(P)](#9P)
      - [Google](#google)
        - [Google Android](#google-android)
        - [Android 5](#android-5)
      - [Samsung](#samsung)
        - [Samsung Android](#samsung-android)
    - [Desktop](#desktop)
      - [Apple](#desktop-apple)
        - [MacOS](#macos)
      - [Microsoft](#microsoft)
        - [Windows 10](#windows10)
      - [Google](#desktop-google)
        - [ChromeOS](#chromeos)
      - [Linux](#linux)
        - [Ubuntu](#ubuntu)
        - [Linux (Firefox Browser Installed)](#linux-firefox)
        - [Linux (Chrome Browser Installed)](#linux-chrome)
      - [Amazon](#amazon)
        - [FireOS](#fireos)   
- [List of captive portal check URLs](#captive-portal-urls)
- [Code of Conduct](#conduct)
- [License](#license)


<a name="existing"></a>
## Existing Device Behavior

<a name="all"></a>
### All

- There are no persistent cookies in CPMB: all the written cookies are destroyed after CPMB closes. [check on Android last changes]

- CPMB closes after authorization is completed (sometimes it needed additional actions from the user)

- The CPMB disappears and the device disconnects from the network when focus is changed to another app, such as SMS or email.

- Most of external services (file system, applications and etc.) are not accessible from CPMB [Add in this section some information about differences between devices behavior in PreAuth vs PostAuth along with some special limitations of CNA and CPMB: memory usage, local storage, JS support and etc.]

<a name="desktop"></a>
### Desktop

<a name="apple"></a>
#### Apple

<a name="ios"></a>
##### iOS

{% include ios.md %}


<a name="ios11"></a>
##### iOS 11+
- (VPN or some other software that blocks Captive Detector Installed)
- Normally, there is a local Push-notification raise instead of CPMB.


<a name="ios6"></a>
##### iOS 6+

- (Switched off the “Auto-connect” selector in the Wi-Fi SSID settings.)
-There is no CPMB rising. Manual redirection is needed.


<a name="google"></a>
#### Google

<a name="google-android"></a>
##### Google Android (Pixel, Pixel2, Pixel3)

- The Android OS determines the existence of the captive portal by attempting to access a list of domains (See appendix for complete list). If the domains are accessible, it can assume that it is not constrained by a captive portal. Otherwise, it will trigger the notification.
- When clicked, users are being redirected to CPMB.
- PostAuth experience – Once a user has successfully authenticated, the mini-browser may be hidden automatically or manually by pressing some special button.

<a name="android-5"></a>
##### Android 5.0.2
- Google Chrome is opened instead of CPMB.

<a name="samsung"></a>
#### Samsung

<a name="samsung-android"></a>
##### Samsung Android

- Active Captive Portal - Notifies user about the need to log in by pushing the OS-level mini browser.
-The Android OS determines the existence of the captive portal by attempting to access a list of domains (See appendix for complete list). If the domains are accessible, it can assume that it is not constrained by a captive portal. Otherwise, it will pops up Captive Portal or Full browser.
-Post-auth experience – Once a user has successfully authenticated, the mini-browser may be hidden automatically or manually by pressing some special button.
-It can be artificial ad block on CPMB in some Android devices.


<a name="desktop"></a>
### Desktop

<a name="desktop-apple"></a>
#### Apple

<a name="macos"></a>
##### MacOS

- Native Mini-Browser – AKA “Captive Network Assistant” (CNA) - Notifies user about the need to log in by pushing the OS-level mini browser.


<a name="microsoft"></a>
#### Microsoft

<a name="windows10"></a>
##### Windows 10

- Notifies user about the need to log in by opening the user’s default browser and attempting to redirect the user to a default HTTP destination which should be intercepted by the network.


<a name="desktop-google"></a>
#### Google

<a name="chromeos"></a>
##### Chrome OS

- Connection manager for Chromium OS attempts to retrieve the web page [http://clients3.google.com/generate_204](ttp://clients3.google.com/generate_204). This well known URL is known to return an empty page with an HTTP status 204. If for any reason the web page is not returned, or an HTTP response other than 204 is received, then shill marks the service as being in the portal state.
- Other captive portals, sometimes run by cellular carriers, provide absolutely no IP connectivity other than to their own servers, but they use a standard DNS server and do not intercept HTTP requests. When a Chrome Book connects to this type of network, the HTTP requests fail because the TCP connection to clients3.google.com can never be established. The portal code tries multiple times for up to 10 seconds to connect to clients3.google.com. If it cannot connect it marks the service as being in a captive portal. This determination is somewhat unreliable because very high latency connections, lossy connections and other network issues can also result in failure to connect to clients3.google.com. All of these are indicative of a network that is not fully functional, but they do not necessarily indicate that the machine is stuck in a captive portal.

<a name="linux"></a>
#### Linux

<a name="ubuntu"></a>
##### Ubuntu

- Doesn’t support OS level captive portal login in available LTS (long term support) releases so far. Now there is a discussion in Ubuntu WiKi networking section where it is proposed to provide OS level support in coming releases. GNOME (GNU Network Object Model Environment) had introduced automatic login prompt for Wi-Fi captive portals (Wi-Fi access points which required web based login, such as those found in public places) quite a while ago. However this functionality is still unavailable in Ubuntu GNOME, The same is part of wish-list in upcoming Ubuntu LTS releases.

<a name="linux-firefox"></a>
#### Linux (Firefox Browser Installed)

- Firefox introduces automatic detection of Captive portals and notifies user about the need to log in. Additionally, after Firefox detects a Captive portal, it replaces certificate error pages with a message encouraging user to log in.
- Firefox determines the existence of a captive portal constraint by attempting to download the file success.txt from http://detectportal.firefox.com/success.txt (there is only one word in that file, the word "success". If it can successfully retrieve that file, it can assume that it is not constrained by a Captive portal. Otherwise, it will trigger an in-browser notification.

<a name="linux-chrome"></a>
#### Linux (Chrome Browser Installed)

-Chrome introduces automatic detection of Captive portals and notifies user about the need to log in. Additionally, after Chrome detects a Captive portal, it replaces certificate error pages with a message encouraging user to log in.

<a name="amazon"></a>
#### Amazon

<a name="fireos"></a>
##### FireOS

- Fire OS (based on Android) uses http://spectrum.s3.amazonaws.com/kindle-wifi/wifistub.html for connectivity checks and if the URI is not reachable, a notification appears indicating a captive portal login is required.
- Tapping the notifications triggers the the captive portal mini-browser to open, the device attempts to reach http://spectrum.s3.amazonaws.com/kindle-wifi/wifiredirect.html and the user is greeted with “Unsecured Connection. This connection is not secure. When using an unsecured connection, your personal information may be visible to others.” After clicking continue, the captive portal loads.
- The Unsecured Connection warning appears to be triggered by the attempt to hit the “wifiredirect” page over HTTP, not because of a TLS certificate mismatch.


<a name="captive-portal-urls"></a>
## List of captive portal check URLs

### Apple iOS
- www.apple.com
- www.appleiphonecell.com
- captive.apple.com
- www.airport.us
- www.ibook.info
- www.itools.info
- www.thinkdifferent.us
- apple.com

### Apple MacOS
- captive.apple.com

### Google Android
- clients3.google.com
- clients4.google.com
- android.clients.google.com
- connectivitycheck.android.com
- connectivitycheck.gstatic.com
- www.gstatic.com
- www.google.com
- www.androidbak.net

### Samsung Android
- http://connectivitycheck.android.com/generate_204
- http://connectivitycheck.gstatic.com/generate_204
- d2uzsrnmmf6tds.cloudfront.net

### HTC Android
- clients3.google.com

### Windows
- msftncsi.com

<a name="conduct"></a>
## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE-OF-CONDUCT.md). By participating in this project you agree to abide by its terms.

<a name="license"></a>
## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [TBD](https://tbd.com/) has waived all copyright and related or neighboring rights to this work.
