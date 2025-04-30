---
title: "Part 1 - Understanding MITRE ATT&CK Enterprise Matrix: Reconnaissance"
date: 2025-01-11
categories: [MITRE]
tags: [ATT&CK, cybersecurity, adversary tactics, techniques, MITRE]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: MITRE ATT&CK framework
---

When I began exploring the MITRE ATT&CK framework in more depth, I decided to dive into each matrix and the tactics listed under them. In today’s post, I’ll be talking specifically about the **Reconnaissance** tactic in the **Enterprise Matrix**.

The Enterprise Matrix includes techniques applicable to several platforms:
- Windows  
- macOS  
- Linux  
- PRE  
- Office Suite  
- Identity Provider  
- SaaS  
- IaaS  
- Network Devices  
- Containers  
- ESXi  

Right now, I’m covering only the 14 tactics and their associated techniques within the **Enterprise Matrix**. I’ll follow this up with other specific matrices in future posts.

### What is Reconnaissance?

**Reconnaissance** is the first tactic in the ATT&CK Enterprise Matrix. It involves gathering information that an adversary can use to plan future operations. These techniques can be either active or passive, and the goal is to collect information about the victim’s organization, infrastructure, or personnel.

Here are some of the common techniques adversaries use during reconnaissance:

---

### 1. **Active Scanning**

This involves the adversary directly interacting with the victim's infrastructure through network traffic. They might scan for open ports, probe systems, or look for vulnerabilities.

**Sub-techniques include:**
- Scanning IP blocks  
- Vulnerability scanning  
- Wordlist scanning  

**Detection & Mitigation:**  
Because reconnaissance occurs outside the defender's control, it's tough to prevent entirely. However, monitoring network traffic for anomalies, protocol deviations, or unexpected patterns can help in detecting such activity.

---

### 2. **Gather Victim Host Information**

This technique focuses on collecting technical data about victim machines.

**Sub-techniques include:**
- **Hardware information** – device type, hardware specs, components that may hint at security tools  
- **Software information** – installed programs, versions, security tools like SIEM, antivirus  
- **Client configuration** – OS type and version, system language, architecture, time zone  

---

### 3. **Gather Victim Identity Information**

Adversaries look for personal or sensitive identity data to aid in attacks. This could be:
- Credentials  
- Email addresses  
- Employee names (to derive usernames or guess passwords)  

---

### 4. **Gather Victim Network Information**

Attackers map out network details, including:
- Network topology  
- Domain properties  
- DNS data  
- IP address space  
- Trust relationships  
- Network appliances and security configurations  

---

### 5. **Gather Victim Organization Information**

Here, the goal is to understand the structure and operations of the target organization.

**Sub-techniques include:**
- Determining physical location  
- Investigating business relationships  
- Identifying business tempo (e.g., busy seasons or hours)  
- Understanding employee roles and responsibilities  

---

### 6. **Phishing for Information**

This involves sending deceptive communications to trick users into revealing sensitive information.

**Sub-techniques include:**
- Spearphishing via services  
- Phishing attachments  
- Phishing links  
- Voice phishing (vishing)  

---

### 7. **Search Closed Sources**

Adversaries may look for information in non-public sources such as:
- Threat intelligence reports  
- Private data dumps  
- Dark web markets  
- Cybercrime forums  

---

### 8. **Search Open Technical Databases**

Publicly available technical repositories can offer valuable insights.

**Examples:**
- DNS records  
- Passive DNS  
- WHOIS databases  
- Digital certificate data  
- Scan databases like Censys or Shodan  

---

### 9. **Search Open Websites or Domains**

Adversaries might scour the internet for info shared on:
- Company websites  
- Social media platforms  
- Online forums  
- Public code repositories (e.g., GitHub)

---

### 10. **Search Victim-Owned Websites**

Attackers often look directly at the organization's own website to learn about:
- Departments and divisions  
- Key personnel  
- Contact details  
- Office locations  
- Organizational structure  

---

This wraps up the first part of my deep dive into the MITRE ATT&CK Enterprise Matrix. In the next parts, I’ll continue exploring the remaining tactics and techniques. Stay tuned!

