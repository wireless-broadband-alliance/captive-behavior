# Captive Network Portal Behavior

> Documentation of captive network portal behavior on different devices

## Background

Public Wi-Fi networks offering temporary internet access often begin new connections using a Captive Portal Mini-Browser (or "CPMB"). These CPMB utilities are built into operating systems in order to make it easier to connect to public Wi-Fi networks. The problem is that their behavior is nuanced, often undocumented and can be difficult to understand. 

The goal for this project is to document captive portal behavior across the various client devices and to hopefully *make it easier to build captive portal solutions that offer a better experience for users*.

## Organized by the WBA

This project is organized by the [Wireless Broadband Alliance](https://www.wballiance.com/) (WBA). The aim of the WBA, together with its 100+ members, is to secure an outstanding user experience through the global deployment of next generation Wireless.

While the WBA organizes this project, anyone is encouraged to contribute. Please see the [contribution guidelines](CONTRIBUTING.md) to learn how or contact the [WBA](https://www.wballiance.com/contact-us/) to find out more.

## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE-OF-CONDUCT.md). By participating in this project you agree to abide by its terms.

### Previewing the project locally

If you'd like to preview the project locally (for example, in the process of proposing a change):

1. Clone down the repository (`git clone https://github.com/wireless-broadband-alliance/captive-behavior.git`)
2. `cd` into the project's directory
3. Run `script/bootstrap` to install the necessary dependencies
4. Run `bundle exec jekyll serve` to start the preview server
5. Visit [`localhost:4000`](http://localhost:4000) in your browser to preview the theme
