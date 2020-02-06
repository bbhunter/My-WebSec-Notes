# My WebSec Notes
Some notes (tips/tricks) gathered by me during time related to web pentesting, bug bounty and browser/tools stuff.  
* P.S.: respectfully cannibalyzed notes from a lot of places: SANS, blog posts... Thank y'all.

## Mozilla Firefox Browser
01) You can use the default Firefox Browser and apply all settings below it will work  same as Firefox Developer Browser.
![](/ff-be.png)

02) You can use Firefox Browser Developer Edition and apply all settings below.
![](/ff-de.png)
--------------------------------------------------------------------------------------------------------------------------------------------
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

* Target > Sitemap > Filters > "show all"
![](/burp-sitemap-filter.png)


* Change Burp Suite Decoder to a local instance of Cyber Chef (https://gchq.github.io/CyberChef/)


--------------------------------------------------------------------------------------------------------------------------------------------

# Domain/Subdomain  
1. Amass **Passive**/**Active**/**Brute** (remember that your config.ini must be configured with API keys)  
1.1 **Passive:** ```amass enum -config config.ini -passive -d <target.com> -o amass-enum-passive-<target.com>.txt -max-dns-queries 2000```  
1.2 **Active:** ```amass enum -config config.ini -active -d <target.com> -p 22,80,443,8080 -o amass-enum-active-<target.com>.txt -max-dns-queries 2000```  
1.3 **Brute:** ```amass enum -config config.ini -brute -d <target.com> -min-for-recursive 4 -o amass-enum-brute-<target.com>.txt -max-dns-queries 2000 -w (/jhaddix/all.txt|/seclists/Discovery/DNS/shubs-subdomains.txt)```  
**TODO** 1.4 Resolvers: include a comprehensive list of DNS resolvers to force find other domains  


Wayback Machine  

Linkfinder  

httprobe  

--------------------------------------------------------------------------------------------------------------------------------------------

# Fingerprint/Technology Detection  
1. WhatWeb
1.1 ./whatweb --input-file targets-list.txt -vv --aggression 4 --max-threads 30
1.2 Massive Banner Grabbing: echo "80,81,300,443,591,593,832,981,1010,1311,2082,2087,2095,2096,2480,3000,3128,3333,4243,4567,4711,4712,4993,5000,5104,5108,5800,6543,7000,7396,7474,8000,8001,8008,8014,8042,8069,8080,8081,8088,8090,8091,8118,8123,8172,8222,8243,8280,8281,8333,8443,8500,8834,8880,8888,8983,9000,9043,9060,9080,9090,9091,9200,9443,9800,9981,12443,16080,18091,18092,20720,28017" | tr ',' '\n' | ./whatweb --aggression 4 --url-pattern target.com:%insert% --input-file /dev/stdin


