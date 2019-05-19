##### FireOS

* Fire OS (based on Android) uses http://spectrum.s3.amazonaws.com/kindle-wifi/wifistub.html for connectivity checks and if the URI is not reachable, a notification appears indicating a captive portal login is required.

* Tapping the notifications triggers the the captive portal mini-browser to open, the device attempts to reach http://spectrum.s3.amazonaws.com/kindle-wifi/wifiredirect.html and the user is greeted with “Unsecured Connection. This connection is not secure. When using an unsecured connection, your personal information may be visible to others.” After clicking continue, the captive portal loads.

* The Unsecured Connection warning appears to be triggered by the attempt to hit the “wifiredirect” page over HTTP, not because of a TLS certificate mismatch.