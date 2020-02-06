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

[Gobuster](https://github.com/OJ/gobuster)  
1. ./gobuster dir -e -u **TARGET** -w **WORDLIST** -v -r -a **'SOME-RANDOM-SHIT/USERAGENT'** -t 20 -l -k -x **"SOME-.EXTENSION"** -f -o **TARGET-OUTPUT.txt**  
```-e: expanded mode,  show full URLs```  
```-u: target URL, only used in DIR mode```  
```-w: path to your wordlist```  
```-v: verbose (always be verbose)```  
```-r: follow redirects (OPTIONAL)```  
```-a: change tour user-agent to some default or random keyword```  
```-t: threads (default is 10)```  
```-l: lenght of the body```  
```-k: skip SSL verification (OPTIONAL)```  
```-x: append the extension (.php, asp, etc) to each request in the wordlist | TIP: first detect what technology the target is using, which language or languages are in use, only then you choose the right extension.```   
```-f: append a forward slash (/) to each request (OPTIONAL)```  
```-o: tool/results output```  


--------------------------------------------------------------------------------------------------------------------------------------------

# Fingerprint/Technology Detection  
1. WhatWeb
1.1 ./whatweb --input-file targets-list.txt -vv --aggression 4 --max-threads 30 



