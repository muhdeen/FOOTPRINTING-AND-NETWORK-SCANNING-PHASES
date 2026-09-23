🌐 Overview
This project documents the footprinting, reconnaissance, and network scanning phases of a penetration testing exercise conducted during Week 2 of my Cybersecurity & Ethical Hacking internship at Networkwalks.
Activities were performed using Kali Linux tools, Maltego, theHarvester, and Zenmap, with proper authorization in a controlled lab environment.
The report demonstrates how security professionals gather public information, map digital assets, and identify active hosts before moving into vulnerability assessment.

🎯 Project Objectives
🔍 Practice and demonstrate the use of multiple Kali Linux tools for footprinting and reconnaissance.

🧩 Apply Maltego and theHarvester for enhanced data collection and relationship mapping.

🌐 Perform authorized network scanning with Zenmap to identify live hosts and create a network topology.

⚠️ Analyze collected information for potential risks and impacts.

📝 Document findings clearly and professionally in a structured penetration testing report.

🛡️ Purpose
The purpose of this project is to strengthen practical skills in ethical hacking by simulating the early stages of a penetration test.
These stages—footprinting, reconnaissance, and scanning—are critical for:

Understanding a target environment

Identifying exposed information

Preparing for deeper security assessments

The exercises also emphasize the importance of authorization, responsible testing, and professional reporting.

📌 Detailed Objectives
📑 Collect publicly available domain and DNS information using WHOIS, Nslookup, Curl, Wafw00f, and DNSRecon.

🕵️ Identify web technologies and potential exposure points with WhatWeb.

🔗 Use Maltego to visualize relationships among domains, IPs, and emails.

📧 Deploy theHarvester to gather emails, subdomains, and hostnames from open sources.

🖥️ Perform local network scanning with Zenmap to detect active hosts and generate a topology.

⚖️ Assess risks based on collected data and propose security recommendations.

✅ Ensure all activities are conducted within authorized scope and documented professionally.

PENETRATION TESTING REPORT
FOOTPRINTING & NETWORK SCANNING PHASES
W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS
Pentester Name (Cybersecurity Professional)	Shamsuddeen Muhammad
Program/Batch	B083-Networkwalks
Date	21 September 2026
Modules completed	W2-PM1 (Multiple Kali Tools)
W2-PM3 (Reaconn with Maltego)
W2-PM4 (Footprint with TheHarvester)
W2-PM5 (Zenmap Scanning)
Client/Target	1.	Networkwalks (secured written permission already)
2.	My own local LAN Network
Permission secured from client?	Yes
Phases covered	Phase 1: Reconnaissance & Footprinting
Phase 2: Scanning & Network Discovery
1.	Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.
2.	Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1) as well as reconnaissance with Maltego(W2-PM3) and The Harvester(W2-PM4), also scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting and reconnaissance phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.
3.	Tools Used
The table below lists each tool used in this report and its purpose.
Tool	Purpose
Kali Linux & Windows	Operating systems used for reconnaissance activities
WHOIS	Find domain registration details (owner, dates, name servers).
whatweb	Fingerprint web technologies (server, CMS, plugins, IP).
nslookup	Resolve the domain name to its IP address using DNS.
curl -I	Read the HTTP response headers of the website.
wafw00f	Detect whether a Web Application Firewall protects the site.
dnsrecon	Enumerate all DNS records (NS, MX, SPF, TXT, SRV).
Maltego	Harvested all email addresses related to the site(networkwalks.com)
The Harvester	Find email id and sub-domain related to the site 
Zenmap (Nmap GUI)	Scan the local subnet to find live hosts, IPs and MAC addresses.
Windows CMD	Local IP and MAC address identification
4.	Activities Performed
4.1	Footprinting & Reconnaissance
I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon.i also deployed the use of Maltego, TheHarvester; Each tool was used to collect a different type of information about the target.
First, I used WHOIS to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.
I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.0.4 and WP Download Manager 3.3.58, along with other information exposed by the website.
Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.
I used Curl with the -I option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint /wp-json/.
Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result identified ModSecurity (SpiderLabs).
 I also used DNSRecon to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.
Then I utilized Maltego to harvest all related email addresses to networkwalks.com 			I Thereafter used The Harvester to get the email-id and sub-domain related to the website.



4.2	Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts.
The example results provided in the practical identified four live hosts:
•	192.168.1.5
•	192.168.1.6
•	192.168.1.16
•	192.168.1.7
The example results also included four MAC addresses.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.

5.	Risk Analysis / Impact
Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.
#	Risk / Finding	Evidence / Observation	Potential Impact	Risk Level
1	Web technology information exposed	WhatWeb identified 
WordPress and WP 
Download Manager	Attackers may use exposed technology/version information to identify software requiring further 
security review	● Medium
2	Server IP address identifiable	Nslookup resolved the domain to 192.232.216.135	Provides information about the network location of the web service	● Low
3	HTTP technical information exposed	Curl returned HTTP response headers and exposed /wp-json/	May assist technology fingerprinting and further enumeration	● Low
4	WAF technology 
identifiable	Wafw00f identified 
ModSecurity 
(SpiderLabs)	Reveals information about the web application’s security architecture	● Low
5	DNS infrastructure information exposed	DNSRecon identified DNS, mail and servicerelated records	DNS information can help build a broader infrastructure profile	● Medium
6	Multiple live hosts 
visible on local network	Zenmap identified four live hosts in the example network	Unknown or unauthorized devices may potentially be present on a network	● Medium
7	Maltego relationship mapping	Maltego visualized links among domains, IPs, and emails	Provides structured view of connected assets, aiding attacker profiling	● Medium
8	TheHarvester data collection	theHarvester gathered emails, subdomains, and hostnames	Expands reconnaissance with publicly available data	● Medium
Risk level key:  ● Critical  ● Medium  ● Low
The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.
The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.
Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.
6.	Recommendations
Based on the observations from these activities, I recommend the following security improvements:
1.	Review publicly exposed technology information
Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.
2.	Keep software updated
CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.
3.	Review HTTP headers
HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.
4.	Review DNS records regularly
DNS records should be checked periodically to ensure that only required information and services are publicly exposed.
5.	Properly configure and monitor the WAF
Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.
6.	Perform regular internal network discovery
Organizations should periodically scan their own networks to identify active devices.
7.	Investigate unknown devices
Any unexpected device discovered during network scanning should be investigated and verified.
8.	Maintain network documentation
Network topology and device information should be documented and updated regularly.
9.	Perform security testing with authorization
Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.
7.	Conclusion
Conclusion
During Week 2 of my Cybersecurity and Ethical Hacking internship, I practiced footprinting, reconnaissance, and network scanning. These activities deepened my understanding of how security professionals gather and analyze information before moving into vulnerability assessment.
For footprinting, I used six Kali Linux tools: WHOIS (domain details), WhatWeb (web technologies), Nslookup (DNS resolution), Curl (HTTP headers), Wafw00f (firewall detection), and DNSRecon (DNS records). Maltego and theHarvester further enhanced reconnaissance by mapping relationships among domains, IPs, and emails, and by collecting public data such as subdomains and hostnames—together providing a structured view of an organization’s digital footprint.
In network scanning, I used Zenmap to identify active hosts, IP/MAC addresses, and create a network topology, showing how scanning reveals devices and connections within an environment.
Overall, these exercises highlighted that information gathering is a critical first step in cybersecurity testing. Clear documentation of findings, their significance, and mitigation recommendations is essential. Finally, all activities must remain within authorized scope, as practiced in the controlled lab environment.
  

 
 
   
 
  
-End👤 Author
Shamsuddeen Muhammad
Cybersecurity Professional B083
 
👤 Project Information
Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: GitHub
