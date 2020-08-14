## Overview

Public Wi-Fi networks offering temporary internet access often begin new connections using a Captive Portal Mini-Browser (or "CPMB"). These CPMB utilities are built into operating systems in order to make it easier to connect to public Wi-Fi networks. The problem is that their behavior is nuanced, often undocumented and can be difficult to understand. 

The goal for this project is to document captive portal behavior across the various client devices and to hopefully *make it easier to build captive portal solutions that offer a better experience for users*.

## Organized by the WBA

<a href="https://wballiance.com/captive-portal-onboarding-evolution/" style="float:right; padding:0 15px 20px 15px;"><img src="/assets/images/wba-logo.png" style="width:200px;"></a>

This project is organized by the [Wireless Broadband Alliance](https://www.wballiance.com/) (WBA). The aim of the WBA, together with its 100+ members, is to secure an outstanding user experience through the global deployment of next generation Wireless. While the WBA organizes this project, anyone is encouraged to contribute. Please see the [GitHub repository](https://github.com/wireless-broadband-alliance/captive-behavior) to learn how or contact the [WBA](https://www.wballiance.com/contact-us/) to find out more.

## Device Database

[Go to Device Database](/device-list.html)

[Go to Device Form](/device-form.html)


## Captive Network Portal Standards Whitepaper

<a href="https://wballiance.com/captive-network-portal-standards/" style="float:right; padding:0 15px;"><img src="/assets/images/captive-portal-standards-whitepaper.png" style="width:170px;"></a>

The [Captive Network Portal Standards whitepaper](https://wballiance.com/captive-network-portal-standards/) defines existing use cases, aligns user experience (UX), presents practices to consider and provides suggested guidelines for future features that can be adopted as a unified standard by client devices, client manufacturers and network hardware manufacturers.

The [Captive Portal - Onboarding Evolution](https://wballiance.com/captive-portal-onboarding-evolution/) WBA workgroup is continuing to focus on improving the user experience of “captivation” and how end-users engage with captive portals in the Passpoint® era. You can learn more about the team behind the Captive Network Portal Standards project and the above whitepaper [here](https://wballiance.com/captive-portal-onboarding-evolution/).

## Contents

- [Connection Process](#connection-process-anchor)
- [Device Behavior Summary](#behavior-summary-anchor)
- [Device Behavior](#device-behavior-anchor)
  - [iOS](#ios-anchor)
  - [Android (Google)](#android-google-anchor)
  - [Android (Samsung)](#android-samsung-anchor)
  - [MacOS](#macos-anchor)
  - [Windows](#windows-anchor)
  - [ChromeOS](#chromeos-anchor)
  - [FireOS](#fireos-anchor)
  - [Linux](#linux-anchor)  
- [List of Captive Portal Check URLs](#urls-anchor)


<a name="connection-process-anchor"></a>
## Connection Process

The connection process for the CPMB usually involves the following steps:

 * Network/Access Point Association
 * Checking connectivity state (detection of Captive Network)
 * Pop-up of a notification (in some cases)
 * Waiting for device activation (if device is in a blocked state)
 * Opening CPMB or waiting for the activation of the notification
 * Checking current connectivity state based on user's action while CPMB is open
 * Closing CPMB after authentication process is completed (automatically or manually)

![CPMB Connection Process Diagram](/assets/images/cpmb-process-diagram.png)


<a name="behavior-summary-anchor"></a>
## Device Behavior Summary (latest versions)

| Platform | Captive Portal Display Method | Default Browser | Details |
| --- | --- |
| iOS | Mini-Browser Popup | Websheet | [More Details](#ios-anchor) |
| Android | Push Notification | Google Chrome | [More Details](#android-google-anchor) |
| Samsung Android | Push Notification | Samsung Internet Browser | [More Details](#android-samsung-anchor) |
| MacOS | Mini-Browser Popup | Safari | [More Details](#macos-anchor) |
| Windows 10 | Manual Browser Redirect | User's Preferred Browser | [More Details](#windows-anchor) |


<a name="device-behavior-anchor"></a>
## Device Behavior

### General Behavior (for most devices)

 * There are no persistent cookies in CPMB: all the written cookies are destroyed after CPMB closes.

 * CPMB closes after authorization is completed (sometimes it requires additional actions from the user)

 * The CPMB disappears and the device disconnects from the network when focus is changed to another app, such as SMS or email.

 * Most external services (file system, applications and etc.) are not accessible from CPMB. There are various differences in device behavior in pre-authenticated vs post-authenticated states, along with many limitations including memory usage, local storage, Javascript support etc.

<a name="ios-anchor"></a>
{% include ios.md %}

<a name="android-google-anchor"></a>
{% include android-google.md %}

<a name="android-samsung-anchor"></a>
{% include android-samsung.md %}

<a name="macos-anchor"></a>
{% include macos.md %}

<a name="windows-anchor"></a>
{% include windows.md %}

<a name="chromeos-anchor"></a>
{% include chromeos.md %}

<a name="linux-anchor"></a>
{% include linux.md %}

<a name="fireos-anchor"></a>
{% include fireos.md %}

<a name="urls-anchor"></a>
{% include urls.md %}
