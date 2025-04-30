---
title: "Part 2 - Understanding MITRE ATT&CK Framework: Resource Development"
date: 2025-01-12
categories: [MITRE]
tags: [ATT&CK, cybersecurity, adversary tactics, techniques, MITRE]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: MITRE ATT&CK framework
---

In this second part of my deep dive into the MITRE ATT&CK framework, we’ll explore the **Resource Development** tactic. This phase involves techniques used by threat actors to **create, purchase, or compromise resources** they can use in later stages of an attack. These resources might include infrastructure, accounts, or custom-built capabilities.

Let’s break down the key techniques under Resource Development:

---

### 1. **Acquire Access**

In this technique, adversaries may **purchase or acquire access** to already compromised systems or networks.  
Often, this is facilitated through **Initial Access Brokers** or other online services that sell access to target environments.  
Sometimes, adversaries may even **collaborate with one another**, sharing compromised systems as a form of partnership.

---

### 2. **Acquire Infrastructure**

Here, the adversary **buys, leases, or rents infrastructure** for use during targeting. This might involve exploiting free trials or renting botnets.  
Infrastructure can include:
- Domains  
- DNS servers  
- VPS (Virtual Private Servers)  
- Cloud or physical servers  
- Web services  
- Serverless platforms  
- Malvertising frameworks  

---

### 3. **Compromise Accounts**

Instead of creating new accounts, attackers may choose to **compromise existing ones**.  
This can build **trust** with the victim, especially if the compromised persona is familiar.  
Accounts at risk include:
- Social media profiles  
- Email accounts  
- Cloud service accounts  

---

### 4. **Compromise Infrastructure**

Rather than renting or buying, adversaries may choose to **illegally take over existing infrastructure**.  
Targets for compromise include:
- Domains  
- DNS servers  
- VPS/cloud/physical servers  
- Botnets  
- Web services  
- Serverless environments  
- Malvertising networks  
- Network devices  

---

### 5. **Develop Capabilities**

In this case, attackers build their own tools rather than obtaining them elsewhere.  
They might develop:
- Custom malware  
- Code signing certificates  
- Exploits  
- Digital certificates  

This gives them more control and helps avoid detection by using tools tailored to their needs.

---

### 6. **Establish Accounts**

Adversaries may **create or cultivate new accounts** to build a fake identity or online presence.  
They might set up:
- Social media profiles  
- Email accounts  
- Cloud service accounts  

This technique is often used to support **social engineering** or impersonation attacks.

---

### 7. **Obtain Capabilities**

Instead of building tools from scratch, attackers might **buy, steal, or freely download capabilities** from various sources.  
These may include:
- Malware  
- Exploits  
- Code signing and digital certificates  
- Security tools  
- AI tools  
- Discovered vulnerabilities  

---

### 8. **Stage Capabilities**

Once the attacker has their tools ready, they may **stage or host them on infrastructure** they control.  
This could involve:
- Uploading malware or tools  
- Installing digital certificates  
- Hosting files for drive-by attacks  
- Creating links to lure targets  
- SEO poisoning to make malicious links appear in search results  

---

That wraps up the **Resource Development** phase in the MITRE ATT&CK framework. In the next part, we’ll explore how these prepared resources are used to gain **Initial Access** to victim environments.


