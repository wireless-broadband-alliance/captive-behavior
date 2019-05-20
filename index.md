## Overview

Public Wi-Fi networks offering temporary internet access often begin new connections using a Captive Portal Mini-Browser (or "CPMB"). These CPMB utilities are built into operating systems in order to make it easier to connect to public Wi-Fi networks. The problem is that their behavior is nuanced, often undocumented and can be difficult to understand. 

The goal for this project is to document captive portal behavior across the various client devices and to hopefully *make it easier to build captive portal solutions that offer a better experience for users*.

## Organized by the WBA

![WBA Logo](/assets/images/wba-logo.png)

This project is organized by the [Wireless Broadband Alliance](https://www.wballiance.com/)(WBA). The aim of the WBA, together with its 100+ members, is to secure an outstanding user experience through the global deployment of next generation Wireless.

While the WBA organizes this project, anyone is encouraged to contribute. Please see the [contribution guidelines](CONTRIBUTING.md) to learn how.


## Contents

- [Connection Process](#connection-process)
- [Device Behavior Summary](#behavior-summary)
- [Device Behavior](#device-behavior)
  - [iOS](#ios)
  - [Android (Google)](#android-google)
  - [Android (Samsung)](#android-samsung)
  - [MacOS](#macos)
  - [Windows](#windows)
  - [ChromeOS](#chromeos)
  - [FireOS](#fireos)
  - [Linux](#linux)  
- [List of Captive Portal Check URLs](#urls)
- [Code of Conduct](#conduct)
- [License](#license)


<a name="connection-process"></a>
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


<a name="behavior-summary"></a>
## Device Behavior Summary (latest versions)

| Platform | Captive Portal Display Method | Default Browser | Details |
| --- | --- |
| iOS | Mini-Browser Popup | Websheet | [More Details](#ios) |
| Android | Push Notification | Google Chrome | [More Details](#android-google) |
| Samsung Android | Push Notification | Samsung Internet Browser | [More Details](#android-samsung) |
| MacOS | Mini-Browser Popup | Safari | [More Details](#macos) |
| Windows 10 | Manual Browser Redirect | User's Preferred Browser | [More Details](#windows) |


<a name="device-behavior"></a>
## Device Behavior

### General Behavior (for most devices)

 * There are no persistent cookies in CPMB: all the written cookies are destroyed after CPMB closes.

 * CPMB closes after authorization is completed (sometimes it requires additional actions from the user)

 * The CPMB disappears and the device disconnects from the network when focus is changed to another app, such as SMS or email.

 * Most external services (file system, applications and etc.) are not accessible from CPMB. There are various differences in device behavior in pre-authenticated vs post-authenticated states, along with many limitations including memory usage, local storage, Javascript support etc.


<a name="ios"></a>
{% include ios.md %}

<a name="android-google"></a>
{% include android-google.md %}

<a name="android-samsung"></a>
{% include android-samsung.md %}

<a name="macos"></a>
{% include macos.md %}

<a name="windows"></a>
{% include windows.md %}

<a name="chromeos"></a>
{% include chromeos.md %}

<a name="linux"></a>
{% include linux.md %}

<a name="fireos"></a>
{% include fireos.md %}

<a name="urls"></a>
{% include urls.md %}


<a name="conduct"></a>
## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE-OF-CONDUCT.md). By participating in this project you agree to abide by its terms.

<a name="license"></a>
## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [TBD](https://tbd.com/) has waived all copyright and related or neighboring rights to this work.
