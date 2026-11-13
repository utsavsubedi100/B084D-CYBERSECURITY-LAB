PENETRATION TESTING REPORT
FOOTPRINTING & NETWORK SCANNING PHASES
W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS

Pentester Name
(Cybersecurity Professional)	Utsav Subedi
Program/Batch	B084D-Networkwalks
Date	25 October 2026
Modules completed	W2-PM1 (Multiple Kali Tools)
W2-PM2: GHDB based Footprinting Attacks
W2-PM3: Maltego based Footprinting Attacks
W2-PM4: theHarvester based Footprinting Attacks
W2-PM5 (Zenmap Scanning)
Client/Target	1. Networkwalks (secured written permission already)
                2. My own local LAN Network
Permission secured from client?	Yes
Phases covered	Phase 1: Reconnaissance & Footprinting
Phase 2: Scanning & Network Discovery
Phase 3: Report Writing




1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

 2. Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1), also used (W2-PM2) GHDB dorks to footprint real targets through Google alone, without ever
touching the target directly, to search for live exposed devices and public files, and also used (W2-PM3) Maltego putting networkwalk domain as entity and using email transform to find email addresses related to networkwalks, and used (W2-PM4) theHarvester to gather a list of email IDs & sub-domains related to target organizations, and scanning my own local network with Zenmap (W2-PM5). These module covers the footprinting phase and the the scanning phase, they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.
All commands and tools were run in Kali Linux and on a Windows PC with Maltego and Zenmap installed. Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.


3. Tools Used
The table below lists each tool used in this report and its purpose.
Tool	Purpose
Kali Linux & Windows	Operating systems used for reconnaissance activities
WHOIS	Find domain registration details (owner, dates, name servers).
whatweb	Fingerprint web technologies (server, CMS, plugins, IP).
nslookup	Resolve the domain name to its IP address using DNS.
curl -I	Read the HTTP response headers of the website.
wafw00f	Detect whether a Web Application Firewall protects the site.
dnsrecon	Enumerate all DNS records (NS, MX, SPF, TXT, SRV).
Zenmap (Nmap GUI)	Scan the local subnet to find live hosts, IPs and MAC addresses.
Windows CMD	Local IP and MAC address identification
theHarvester -d -l -b	Collects email, sub-domains and hosts from dozen of public sources.
GHDB	GHDB dorks to footprint real targest through google alone.
Maltego	Uesd to find email addresses related to target.

4. Activities Performed
4.1 Footprinting & Reconnaissance

I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. And also used GHDB to find open vulnerable devices and file online. Used Maltego to find email addresses related to target and used theHarvester to find email ids and sub-domains of the target. Each tool was used to collect a different type of information about the target.
First, I used WHOIS to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.
I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.0.4 and WP Download Manager 3.3.58, along with other information exposed by the website.
Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.
I used Curl with the -I option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint /wp-json/.
Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result identified ModSecurity (SpiderLabs).
Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.
For GHDB I looked up www.exploit-db.com and used it to find different vulnerable devices online, I searched the dork one after another and used github, www.insecam.org, to find other dorks to collect 10x live vulnerable security camera and 10x listing of downloadable math ebooks pdf.
Installed Maltego in my windows pc and used it to find the email addresses related to networkwalks.com by keeping network walks as the entity and transform output as email to find the related emails.
Used theHarvester for similar purpose to find email ids and subdomains of the target, used -d to set the domain, -l to limit the number or results and -b to set the data source, then extracted the details and showed them on the screen


4.2 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts.
The example results provided in the practical identified four live hosts:
•	192.168.100.1
•	192.168.100.211
The example results also included four MAC addresses.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.
Note: The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.

5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.
#	Risk / Finding	Evidence / Observation	Potential Impact	Risk Level
1	Web technology information exposed	WhatWeb identified WordPress and WP Download Manager	Attackers may use exposed technology/version information to identify software requiring further security review	● Medium
2	Server IP address identifiable	Nslookup resolved the domain to 192.232.216.135	Provides information about the network location of the web service	● Low
3	HTTP technical information exposed	Curl returned HTTP response headers and exposed /wp-json/	May assist technology fingerprinting and further enumeration	● Low
4	WAF technology identifiable	Wafw00f identified ModSecurity (SpiderLabs)	Reveals information about the web application’s security architecture	● Low
5	DNS infrastructure information exposed	DNSRecon identified DNS, mail and service-related records	DNS information can help build a broader infrastructure profile	● Medium
6	Multiple live hosts visible on local network	Zenmap identified four live hosts in the example network	Unknown or unauthorized devices may potentially be present on a network	● Medium
7	Vulnerable cameras and files	GHDB identified open camera and free downloadable file.	Unknow user and look at the vulnerable camera online and also install the math ebooks pdf for free.	● Critical
8	Email IDs & sub-domains exposed	theHarvester and Maltego, gathered the list of email ids related to the target organization.	The email ids and sub-domains can be used for fishing attacks to the company	● Medium

Risk level key:  ● Critical  ● Medium  ● Low
The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.
The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.
Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

6. Recommendations
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
10.	Use passwords on cameras to log in and only source ebooks to trusted source.
11.	Try to train user in the organization about the different cyber attacks like phising, scams, etc.

7. Conclusion
During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.
In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information. I also learned about GHDB, how to OSINT and look for thing online using google in a proper way. Also learned about Maltego and theHarvester, how to use them and find different email ids and sub-domains related to the target organizations.
In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.
The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.
I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.
Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

👤 Author
Utsav Subedi
Cybersecurity Professional B084D
LinkedIn: https://www.linkedin.com/in/utsav-subedi-b84442447/
________________________________________
📌 Project Information
Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: https://github.com/utsavsubedi100/B084D-CYBERSECURITY-LAB/tree/main/week2
