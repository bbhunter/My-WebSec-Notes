# My WebSec Notes
Some notes (tips/tricks) gathered by me during time related to web pentesting, bug bounty and browser/tools stuff.  
* P.S.: respectfully cannibalyzed notes from a lot of places: SANS, blog posts... Thank y'all.

# Mozilla Firefox Browser
01) You can use the default Firefox Browser and apply all settings below it will work  same as Firefox Developer Browser.
![](/ff-be.png)

02) You can use Firefox Browser Developer Edition and apply all settings below.
![](/ff-de.png)

### Firefox params for a more "silent" browser
![](/ff-about.png)

**Allow Weak SSL Ciphers and Protocols:** ```security.tls.version.min = 0```  

**Allow Mixed Content:** ```security.mixed_content.block_active_content = disable```  

**Disable XSS Protection:** ```browser.urlbar.filter.javascript```  

**Disable Captive Web Portal Tester:** ```network.captive-portal-service```  

**Disable Automaticakky Googling and Suggesting:** ```browser.urlbar.autocomplete.enabled```  or  ```browser.urlbar.autoFill```

**Disable Telemetry:** ```toolkit.telemetry.enabled```  

**Disable OSCP Stapling:** ```security.ssl.errorReporting.enabled = disable```  

**Disable Normandy:** ```app.normandy.enabled = false```  

**Disable Activity Stream:** ```browser.library.activity-stream.enabled```  

**Disable Safebrowsing Features:**  
	```browser.safebrowsing.blockedURIs.enabled```  
	```browser.safebrowsing.downloads.enabled```  
	```browser.safebrowsing.downloads.remote.enabled```  
	```browser.safebrowsing.malware.enabled```  
	```browser.safebrowsing.phishing.enabled```  

**More Telemetry:**  
	```browser.newtabpage.activity-stream.feeds.telemetry```  
	```browser.newtabpage.activity-stream.telemetry```  
	```browser.ping-centre.telemetry```  
	```browser.safebrowsing.blockedURIs.enabled```  
	```datareporting.healthreport.uploadEnabled```  
	```plugins.flashBlock.enabled```  
	```privacy.trackingprotection.annotate_channels```  
	```privacy.trackingprotection.enabled```  
	```privacy.trackingprotection.pbmode.enabled```  
	```toolkit.telemetry.archive.enabled```  
	```toolkit.telemetry.enabled```  




# Burp Suite Community/Pro

Target > Sitemap > Filters > "show all"
![](/burp-sitemap-filter.png)


Change Burp Suite Decoder to a local instance of Cyber Chef (https://gchq.github.io/CyberChef/)
