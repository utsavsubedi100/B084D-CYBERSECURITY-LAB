# PENETRATION TESTING REPORT
## Footprinting & Network Scanning Phases
### W2-PM-FINAL | Cybersecurity | Networkwalks

---

## 1. Project Information

| Field | Details |
|---|---|
| **Pentester Name** | Utsav Subedi |
| **Program / Batch** | B084D – Networkwalks |
| **Date** | 25 October 2026 |
| **Client / Target** | 1. Networkwalks (secured written permission already) <br> 2. My own local LAN Network |
| **Permission Secured?** | Yes |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting <br> Phase 2: Scanning & Network Discovery <br> Phase 3: Report Writing |

### Modules Completed

- W2-PM1 – Multiple Kali Tools
- W2-PM2 – GHDB-Based Footprinting Attacks
- W2-PM3 – Maltego-Based Footprinting Attacks
- W2-PM4 – theHarvester-Based Footprinting Attacks
- W2-PM5 – Zenmap Scanning

---

## 2. Liability Disclaimer

I have performed these activities only on systems and devices where I had secured written permission or on devices and systems that I own myself.

All these materials are for educational and research purposes only. Do not use anything from here to break the law.

The instructor, the authors, and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility.

Misuse can lead to criminal charges, heavy fines, loss of your job, and a permanent record. In most countries, unauthorized access is a crime even when nothing is damaged.

---

## 3. Introduction

This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1).

I also used:

- **W2-PM2:** GHDB dorks to footprint real targets through Google alone, without ever touching the target directly, to search for live exposed devices and public files.
- **W2-PM3:** Maltego, putting the Networkwalks domain as an entity and using email transforms to find email addresses related to Networkwalks.
- **W2-PM4:** theHarvester to gather a list of email IDs and subdomains related to target organizations.
- **W2-PM5:** Zenmap to scan my own local network.

These modules cover the footprinting phase and the scanning phase. They show how an attacker moves from gathering public information to mapping live hosts on a network.

This is the Week 2 part of my ongoing internship program at Networkwalks.

All commands and tools were run in Kali Linux and on a Windows PC with Maltego and Zenmap installed.

Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

---

## 4. Tools Used

The table below lists each tool used in this report and its purpose.

| Tool | Purpose |
|---|---|
| Kali Linux & Windows | Operating systems used for reconnaissance activities. |
| WHOIS | Find domain registration details (owner, dates, name servers). |
| WhatWeb | Fingerprint web technologies (server, CMS, plugins, IP). |
| Nslookup | Resolve the domain name to its IP address using DNS. |
| Curl | Read the HTTP response headers of the website. |
| Wafw00f | Detect whether a Web Application Firewall protects the site. |
| DNSRecon | Enumerate DNS records (NS, MX, SPF, TXT, SRV). |
| Zenmap (Nmap GUI) | Scan the local subnet to find live hosts, IPs, and MAC addresses. |
| Windows CMD | Local IP and MAC address identification. |
| theHarvester | Collect email addresses, subdomains, and hosts from public sources. |
| GHDB | Use GHDB dorks to footprint real targets through Google alone. |
| Maltego | Find email addresses related to the target. |

---

## 5. Activities Performed

### 5.1 Footprinting & Reconnaissance

I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon.

I also used GHDB to find open vulnerable devices and files online. Maltego was used to find email addresses related to the target, while theHarvester was used to find email IDs and subdomains of the target.

Each tool was used to collect a different type of information about the target.

#### 5.1.1 WHOIS

First, I used WHOIS to obtain publicly available domain registration information and identify the domain's name servers.

The results provided information about the domain registration and hosting infrastructure.

#### 5.1.2 WhatWeb

I then used WhatWeb to identify technologies used by the website.

The results identified:

- WordPress 7.0.4
- WP Download Manager 3.3.58
- Other information exposed by the website.

#### 5.1.3 Nslookup

Using Nslookup, I resolved the domain name to its IP address.

**Result:** `192.232.216.135`

#### 5.1.4 Curl

I used Curl with the `-I` option to inspect the HTTP response headers.

This provided additional information about the web application and exposed the WordPress REST API endpoint:

`/wp-json/`

#### 5.1.5 Wafw00f

Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website.

**Result:** ModSecurity (SpiderLabs).

#### 5.1.6 DNSRecon

Finally, I used DNSRecon to enumerate DNS records.

The results provided information relating to:

- Name servers
- Mail servers
- SPF/TXT records
- Service records
- DNS software information

#### 5.1.7 GHDB – Google Hacking Database

For GHDB, I looked up [Exploit Database](https://www.exploit-db.com/) and used it to find different vulnerable devices online.

I searched the dorks one after another and used GitHub and [Insecam](https://www.insecam.org/) to find other dorks.

Using these searches, I collected:

- 10 live vulnerable security cameras.
- 10 listings of downloadable math ebooks in PDF format.

#### 5.1.8 Maltego

I installed Maltego on my Windows PC and used it to find email addresses related to networkwalks.com.

I kept Networkwalks as the entity and used the transform output as email to find the related email addresses.

#### 5.1.9 theHarvester

I used theHarvester for a similar purpose: finding email IDs and subdomains related to the target organization.

I used:

- `-d` to set the domain.
- `-l` to limit the number of results.
- `-b` to set the data source.

I then extracted the details and displayed them on the screen.

---

### 5.2 Network Scanning with Zenmap

For the second activity, I used Zenmap to perform network discovery on my local network.

The practical required me to:

- Identify my local IP address and subnet.
- Discover live hosts.
- Identify their IP and MAC addresses.
- Generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet.

I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.

The example results provided in the practical identified four live hosts:

- `192.168.100.1`
- `192.168.100.211`

The example results also included four MAC addresses.

After completing the scan, I opened the Topology section in Zenmap, enabled the legend, and saved the network topology in PDF format as required by the practical task.

**Note:** The actual subnet, number of hosts, and addresses should be replaced with the results from my own network when submitting the report.

---

## 6. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager. | Attackers may use exposed technology/version information to identify software requiring further security review. | Medium |
| 2 | Server IP address identifiable | Nslookup resolved the domain to `192.232.216.135`. | Provides information about the network location of the web service. | Low |
| 3 | HTTP technical information exposed | Curl returned HTTP response headers and exposed `/wp-json/`. | May assist technology fingerprinting and further enumeration. | Low |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs). | Reveals information about the web application's security architecture. | Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail, and service-related records. | DNS information can help build a broader infrastructure profile. | Medium |
| 6 | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network. | Unknown or unauthorized devices may potentially be present on a network. | Medium |
| 7 | Vulnerable cameras and files | GHDB identified open cameras and free downloadable files. | Unknown users can look at vulnerable cameras online and also install the math ebooks PDF for free. | Critical |
| 8 | Email IDs & subdomains exposed | theHarvester and Maltego gathered a list of email IDs related to the target organization. | The email IDs and subdomains can be used for phishing attacks against the company. | Medium |

### Risk Level Key

- 🔴 **Critical**
- 🟠 **Medium**
- 🟢 **Low**

The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address, or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

---

## 7. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

### 7.1 Review Publicly Exposed Technology Information

Organizations should regularly review what information about their web technologies, CMS, and plugins is publicly visible.

### 7.2 Keep Software Updated

CMS platforms, plugins, and other web technologies should be regularly updated and reviewed against current security advisories.

### 7.3 Review HTTP Headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 7.4 Review DNS Records Regularly

DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

### 7.5 Properly Configure and Monitor the WAF

Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.

### 7.6 Perform Regular Internal Network Discovery

Organizations should periodically scan their own networks to identify active devices.

### 7.7 Investigate Unknown Devices

Any unexpected device discovered during network scanning should be investigated and verified.

### 7.8 Maintain Network Documentation

Network topology and device information should be documented and updated regularly.

### 7.9 Perform Security Testing with Authorization

Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

### 7.10 Secure Internet-Connected Cameras

Use passwords on cameras to log in and only source ebooks from trusted sources.

### 7.11 Provide Cybersecurity Awareness Training

Try to train users in the organization about different cyberattacks like phishing, scams, etc.

---

## 8. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance, and network scanning.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.

I also learned about GHDB, how to perform OSINT, and how to look for things online using Google in a proper way. I also learned about Maltego and theHarvester, how to use them, and how to find different email IDs and subdomains related to target organizations.

In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.

Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope.

These activities were completed as part of the assigned educational cybersecurity lab.

---

## 9. Author Information

**Utsav Subedi**  
Cybersecurity Professional  
Program / Batch: B084D – Networkwalks

**LinkedIn:** [Utsav Subedi](https://www.linkedin.com/in/utsav-subedi-b84442447/)

---

## 10. Project Information

| Field | Details |
|---|---|
| **Program** | Cybersecurity Program at Networkwalks |
| **Week** | Week 02 |
| **Project** | W2-PM-FINAL |
| **Repository** | [B084D-CYBERSECURITY-LAB – Week 2](https://github.com/utsavsubedi100/B084D-CYBERSECURITY-LAB/tree/main/week2) |

---

**End of Report**
