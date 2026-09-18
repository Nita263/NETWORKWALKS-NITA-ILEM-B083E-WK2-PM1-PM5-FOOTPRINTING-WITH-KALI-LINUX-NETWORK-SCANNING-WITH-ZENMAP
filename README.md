# Penetration Testing Report 
Footprinting &amp; network scanning phases (Kali Linux and Zenmap)


| Field | Details |
| :--- | :--- |
| **Pentester Name** | Nita Ilem |
| **Batch** | B083E \| NetworkWalks Cybersecurity Internship |
| **Date** | 18th September 2026 |
| **Modules Completed** | W2-PM1: Kali Linux based Footprinting<br>W2-PM5: Network Scanning with Zenmap |
| **Client / Target** | 1. `networkwalks.com` (written permission secured)<br>2. My own local VirtualBox host-only LAN |
| **Permission Secured** | ✅ Yes |
| **Phases Covered** | Phase 1: Footprinting & Reconnaissance with Kali Linux<br>Phase 2: Network Scanning with Zenmap<br>Phase 3–5: In Progress |

## 1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorized access is a crime even when nothing is damaged.

## 2. Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. This is Week 2 part of my ongoing internship program at Networkwalks.
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

## 3. Tools Used
The table below lists each tool used in this report and its purpose.
| Tools | Purpose |
| :---| :--- |
| Kali Linux & Windows | Operating systems used for reconnaissance activities.
| WHOIS | Query public domain registration (name, owner, date, server).
| Whatweb | Fingerprint technologies running on the website (frameworks, servers CMS, plugins, IP).
| nslookup | Resolve domain name to it´s IP address usimg DNS.
| curl -I | Read HTTP response headers to see the server banner, status, cookies and redirects.
| Wafw00f | Detects if a Web Application Firewall is protecting the site.
| dnsrecon | Enumerates all DNS records (Mail servers, SPF, TXT SRV).
| Zenmap (Nmap GUI) | Scan the local subnet to find live hosts, IPs and MAC addresses.
| Windows CMD | Local IP and MAC address identification

# 4. Activities Performed
4.1 Footprinting & Reconnaissance

I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target.

First, I used WHOIS to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.

I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.1 and WP Download Manager 3.3.58, along with other information exposed by the website.

Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.

I used Curl with the -I option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint /wp-json/.

Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result showed that the site seemed to be behind a WAF or some sort of security solution.

Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers (Hostgator.com), mail servers, SPF/TXT records, service records and DNS software information.

# 4.2 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected quick Scan from the drop down, then click on scan to identify active hosts.

The results provided in the practical identified one live host:
•	172.20.10.3

After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.

## 5. Risk Analysis / Impact
Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.


| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager | Attackers may use exposed technology/version information to identify software requiring further security review | 🟠 Medium |
| 2 | Server IP address identifiable | Nslookup resolved the domain to 192.232.216.135 | Provides information about the network location of the web service | 🟡 Low |
| 3 | HTTP technical information exposed | Curl returned HTTP response headers and exposed /wp-json/ | May assist technology fingerprinting and further enumeration | 🟡 Low |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the web application's security architecture | 🟡 Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail and service-related records | DNS information can help build a broader infrastructure profile | 🟠 Medium |




