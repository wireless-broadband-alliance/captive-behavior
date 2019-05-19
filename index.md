## Purpose

Public Wi-Fi networks offering temporary internet access commonly begin new connections using a Captive Portal Mini-Browser (or "CPMB"). These utilities are built into operating systems in an attempt to make it easier to connect to public Wi-Fi networks. The problem is that their behavior is nuanced, largely undocumented and changes frequently. The aim for this project is to document how client devices behave in captive portal environments.

## Background

This also happens in fixed and cellular networks in the case of insufficient balance for prepaid tariff plans. Each platform has a native version that is "baked" into the OS. There are also commercial browsers, like Firefox and Chrome that have built-in support to detect and navigate to the Captive Portal. This mode uses a web-view pushed to the client and has limited capabilities for branding, advertising and other monetization tactics along with limited capabilities with special authorization processes and paid access.

The aim for this project 


## Behavior Overview (latest versions only)

| Platform | Connection Method | Default Browser | Details |
| --- | --- |
| iOS | Mini-Browser | Websheet | [More Details](#ios) |
| Android | :white_check_mark: | :x: | [More Details](#google-android) |
| Samsung Android | :white_check_mark: | :x: | [More Details](#samsung-android) |
| MacOS | :white_check_mark: | :x: | [More Details](#macos) |
| Windows 10 | :white_check_mark: | :x: | [More Details](#windows10) |


## Contents

- [Existing Device Behavior](#existing)
  - [iOS](#ios)
  - [Android (Google)](#android-google)
  - [Android (Samsung)](#android-samsung)
  - [MacOS](#macos)
  - [Windows](#windows)
  - [ChromeOS](#chromeos)
  - [FireOS](#fireos)
  - [Linux](#linux)  
- [List of Captive Portal Check URLs](#urls)
- [How to Contribute](#contribute)
- [Code of Conduct](#conduct)
- [License](#license)


<a name="existing"></a>
## Existing Device Behavior

 * There are no persistent cookies in CPMB: all the written cookies are destroyed after CPMB closes.

 * CPMB closes after authorization is completed (sometimes it needed additional actions from the user)

 * The CPMB disappears and the device disconnects from the network when focus is changed to another app, such as SMS or email.

 * Most of external services (file system, applications and etc.) are not accessible from CPMB. There are various differences in device behavior in pre-authentiecated vs post-authenticated states, along with many limitations including memory usage, local storage, Javascript support etc.


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

<a name="captive-portal-urls"></a>
{% include urls.md %}


<a name="contribute"></a>
## How to Contribute

Find something that needs to be updated or want to add more details for a specific platform? Please do! More details coming soon on how to contribute.

<a name="conduct"></a>
## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE-OF-CONDUCT.md). By participating in this project you agree to abide by its terms.

<a name="license"></a>
## License

[![CC0](http://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [TBD](https://tbd.com/) has waived all copyright and related or neighboring rights to this work.
