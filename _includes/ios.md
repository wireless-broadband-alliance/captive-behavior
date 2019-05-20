
##### iOS (latest)

 * Standard flow for Captive Network authorization process starts from Wi-Fi association. It doesn’t matter what kind of Wi-Fi association protocol is used (Hotspot 2.0 or other): in all cases just after the association is complete, the device making a request for IP-address (DHCP DISCOVER).

 * After receiving of IP-address the device goes to check `http://captive.apple.com/hotspot-detect.html` (exact domain and URI could be different from this one: see appendix for complete list) via so-called CNA Helper. 

 * In this request the device uses specific User-Agent: “CaptiveNetworkSupport-355.200.27 wispr” (the version mentioned could be different). Received answer is analyzing for Web-authorization existence and in case of detection, Wi-Fi network marks as captivated (appropriate switches appears in the network settings), and switching from cellular connection to Wi-Fi doesn’t appear otherwise the device switches to the Wi-Fi connection as major one.

 * In case of association with known SSID of Captive Network when device is not active (locked state in a pocket, for example), there is no further requests produced by device before unlocking. After this device is unlocked, additional checking request appears and in case of Web-authorization confirms, CPMB is rising.

 * When CPMB is risen it generate additional request to http://captive.apple.com/hotspot-detect.html (see appendix for complete list) but with different kind of User-Agent: “Mozilla/5.0 (iPhone; CPU iPhone OS 12_0 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Mobile/16A366” (the version mentioned could be different). During authorization process in CPMB, almost all network actions followe4d by additional checks of current state.

 * When the CPMB detects that the captive domain is accessible, it changes the control button in the top right corner from “Cancel” to “Done” and switches the primary connection from cellular network to Wi-Fi. The CPMB only performs a check of the captive domain after a full URL navigation or by timer. A javascript-triggered AJAX call for example will not result in the CPMB performing an additional check of the captive domain. With a single page app that does not redirect to a separate post-authentication landing page, a full page navigation must occur for the CPMB to change the control button from “Cancel’ to “Done”. If this doesn’t happen, the user’s device will be authenticated and connected to Wi-Fi but the CPMB will only provide the “Cancel” option, which will disassociate the device from the SSID and take the user back the Wi-Fi network selection screen in the Settings menu.

 * Sometimes, after several connections to the Wi-Fi network without Captive Portal with the same SSID as used in Captive Network, iOS may switch off Captive Checker for this particular SSID and there will no Captive Browser rising

##### iOS
 > With VPN or some other software that blocks Captive Detector Installed
 * Normally, there is a local Push-notification raise instead of CPMB.
 * Observed in iOS 11+

##### iOS
 > With "Auto-connect" selector in the Wi-Fi SSID settings switched off.
 * The CPMB does not display automatically. Manual redirection from a browser is needed.
 * Observed in iOS 6+
