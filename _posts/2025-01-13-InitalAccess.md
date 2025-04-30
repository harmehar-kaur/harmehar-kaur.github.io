---
title: "Part 3 - Understanding MITRE ATT&CK Framework: Initial Access"
date: 2025-01-13
categories: [MITRE]
tags: [ATT&CK, cybersecurity, adversary tactics, techniques, MITRE]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: MITRE ATT&CK framework
---

The **Initial Access** tactic includes techniques that adversaries use to gain their **first foothold** within a target network. This could be through methods like **targeted spearphishing** or by **exploiting vulnerabilities in public-facing systems**. That initial access might lead to prolonged presence or just temporary, limited control.

There are **10 core techniques** associated with this tactic. Let’s explore them:

---

### 1. **Content Injection**

Instead of luring victims to malicious content hosted elsewhere, the attacker may **inject malicious data directly into a legitimate communication channel**—such as modifying traffic or manipulating content that users interact with—effectively tricking them into executing or downloading something harmful.

---

### 2. **Drive-by Compromise**

In this technique, access is gained simply when a **user visits a compromised website** during normal browsing activity. The attacker uses vulnerabilities in the browser or plugins to automatically deliver a payload, without requiring the user to actively download or click anything.

---

### 3. **Exploitation of Public-Facing Applications**

Adversaries often target **internet-facing applications**, looking for **software bugs, misconfigurations, or temporary flaws**. These weaknesses can be exploited to gain direct access to internal systems or to pivot deeper into the environment.

---

### 4. **External Remote Services**

Here, attackers take advantage of **remote access tools** like:
- Remote Desktop Protocol (RDP)  
- VPNs  
- VNC  
- Citrix  
- Windows Remote Management  

By exploiting weak credentials, configuration issues, or exposed services, they gain initial or even persistent access.

---

### 5. **Hardware Additions**

Rather than relying on malware alone, a threat actor might introduce **malicious hardware components or accessories** into a system—like network devices or peripheral add-ons—designed to offer backdoor access or unauthorized functionality.

---

### 6. **Phishing**

Phishing remains one of the most popular methods of gaining initial access. Attackers send **deceptive emails or messages** that trick users into clicking on malicious links or opening dangerous attachments.

**Sub-techniques include:**
- Phishing attachments  
- Phishing links  
- Spearphishing via third-party services  
- Spearphishing with fake invoices or requests  

---

### 7. **Removable Media**

Adversaries may use **removable storage devices** (like USB drives) to deliver malware. This can happen in multiple ways:
- Auto-run malware upon insertion  
- Manually placed payloads  
- Firmware-level tampering or formatting manipulation  

---

### 8. **Supply Chain Compromise**

Sometimes attackers target the **software or hardware supply chain** itself—long before the product reaches the victim. They might:
- Modify software dependencies or code libraries  
- Compromise development tools  
- Tamper with the hardware supply chain  

The idea is to embed malicious components during production or delivery.

---

### 9. **Trusted Relationships**

Threat actors may abuse **existing connections or relationships** between organizations. If one company has access to another’s systems (e.g., through support contracts, partnerships, or remote management), compromising the first can lead to access to the second.

These connections often have **less monitoring or fewer defenses**, making them attractive paths for intrusion.

---

### 10. **Valid Accounts**

Finally, attackers may simply **use legitimate credentials** to access systems. These credentials could be:
- Stolen from prior breaches  
- Default or weak passwords  
- Purchased from underground markets  

They might belong to:
- Local accounts  
- Domain accounts  
- Cloud accounts  

Once inside, these valid accounts can be used to escalate privileges or maintain persistent access.

---

That wraps up the **Initial Access** phase in the MITRE ATT&CK framework. In the next part, we'll explore what adversaries do **once they’re inside** the network.

Stay tuned for Part 4!
