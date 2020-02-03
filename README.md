# My-WebSec-Notes
Some notes of mine (tips/tricks) related to web pentesting and bug bounty stuff

# Mozilla Firefox Browser
01) You can use the default Firefox Browser and apply all settings below it will work  same as Firefox Developer Browser.
02) You can use Firefox Browser Developer Edition and apply all settings below.

##### Firefox params for a more "silent" browser
Allow Weak SSL Ciphers and Protocols: security.tls.version.min = 0
Allow Mixed Content: security.mixed_content.block_active_content = disable
Disable XSS Protection: browser.urlbar.filter.javascript
Disable Captive Web Portal Tester: network.captive-portal-service
Disable Automaticakky Googling and Suggesting: browser.urlbar.autocomplete.enabled
Disable Telemetry: toolkit.telemetry.enabled
Disable OSCP Stapling: security.ssl.error reporting.enabled = disable
Disable Normandy: app.normandy.enabled = false
Disable Activity Stream: browser.library.activity-stream.enabled
Disable Safebrowsing Features:
	browser.safebrowsing.blockedURIs.enabled
	browser.safebrowsing.downloads.enabled
	browser.safebrowsing.downloads.remote.enabled
	browser.safebrowsing.malware.enabled
	browser.safebrowsing.phishing.enabled
More Telemetry:
	browser.newtabpage.activity-stream.feeds.telemetry
	browser.newtabpage.activity-stream.telemetry
	browser.ping-centre.telemetry
	browser.safebrowsing.blockedURIs.enabled
	datareporting.healthreport.uploadEnabled
	plugins.flashBlock.enabled
	privacy.trackingprotection.annotate_channels
	privacy.trackingprotection.enabled
	privacy.trackingprotection.pbmode.enabled
	toolkit.telemetry.archive.enabled
	toolkit.telemetry.enabled
