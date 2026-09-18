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
