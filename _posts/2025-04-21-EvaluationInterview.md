---
title: Evaluation Interview
date: 2025-04-21
categories: [Cyber Security Fundamentals]
tags: [Evaluation interview, SQL injection, Input sanitization, Broken access control, UAC]
author: Harmehar Kaur 
image:
  path: /assets/cyber-prefix.jpg
  alt: Cyber Security Banner
---

# Evaluation Interview

Today, I had an evaluation meeting for my current internship. After my presentation, I was asked a few technical questions. I also gathered some additional ones from peers who went through similar interviews. So, I thought — why not consolidate everything into one place as a blog post? It’ll be super handy for future reference.

---

## 🔐 How to mitigate Security Misconfiguration, SQL Injection, and Broken Access Control?

**Security Misconfiguration**
- Disable unused features and services.
- Regularly patch and update systems.
- Use secure default configurations.
- Implement proper logging and alerting mechanisms.

**SQL Injection**
- Use parameterized queries or prepared statements.
- Validate and sanitize user inputs.
- Prefer ORM libraries for database interactions.
- Suppress detailed error messages in production.

**Broken Access Control**
- Apply Role-Based Access Control (RBAC).
- Do not rely on client-side authorization.
- Enforce access checks on every request.
- Conduct regular access control testing.

---

## 🚨 How to deal with false positives?

- Tune detection signatures and rules.
- Use threat intelligence to filter known safe behavior.
- Maintain a whitelist for verified sources or actions.
- Review alerts periodically and update configurations.

---

## 📈 Anomaly Detection Algorithms

- **Statistical Methods**: Z-score, standard deviation, moving average.
- **Machine Learning**: One-Class SVM, Isolation Forest, Autoencoders.
- **Clustering**: K-Means, DBSCAN.
- **Time Series Analysis**: ARIMA, LSTM networks.

These algorithms help in identifying unusual behavior that could indicate threats.

---

## 🌐 Common Threats on the Dark Web

- Leaked credentials and data dumps.
- Malware and ransomware toolkits.
- Illicit marketplaces (drugs, weapons, fake IDs).
- Fraud services like carding and phishing kits.
- Exploits and zero-day vulnerabilities.

---

## 🧅 What is the Tor Network and Which Algorithms Does it Use?

**Purpose**: Tor anonymizes internet traffic by routing it through multiple nodes using layered encryption (onion routing).

**Algorithms Used**:
- **RSA** for asymmetric encryption.
- **AES** for symmetric encryption.
- **Diffie-Hellman** for secure key exchange.
- **SHA-1/SHA-256** for hashing and integrity.

Tor hides both the source and destination of traffic for privacy and security.

---

## 🔍 Correlating Certificate Transparency (CT) Logs with Chrome/Firefox

- Chrome and Firefox use CT logs to verify SSL/TLS certificates.
- Use tools like [crt.sh](https://crt.sh/) or Google’s CT log dashboard.
- DevTools in Chrome (Security tab) shows CT log status of a site.
- Match SCT (Signed Certificate Timestamp) from the certificate with entries in public logs.

---

## 🧪 Limitations of Nmap in a Home Lab

- Limited visibility in virtualized NAT environments.
- Some scan types require root/administrator access.
- May miss services on non-standard ports.
- IDS/IPS can block or alert on Nmap scans.
- Doesn’t detect application-level vulnerabilities.

---

## 🏛️ Main Components of Active Directory

- **Domain Controllers (DCs)** – Manage AD data and authentication.
- **Users and Computers** – The core objects stored in AD.
- **Organizational Units (OUs)** – Logical containers for grouping.
- **Group Policy Objects (GPOs)** – Policies applied to users/computers.
- **Trusts** – Relationships between different domains/forests.

---

## 🖥️ Domain vs Workgroup

| Feature              | Domain                          | Workgroup                      |
|----------------------|----------------------------------|--------------------------------|
| Management           | Centralized (via AD)             | Decentralized (per device)     |
| User Authentication  | Centralized                      | Local to each machine          |
| Scalability          | Supports large networks          | Best for small setups          |
| Security             | High (policies, GPOs)            | Basic                          |

---

## 🦠 Types of Malware That Can Be Analyzed

- **Viruses** – Infect and modify legitimate files.
- **Worms** – Self-replicating malware that spreads over networks.
- **Trojans** – Malicious programs disguised as legitimate.
- **Ransomware** – Encrypts files and demands ransom.
- **Rootkits** – Hide the presence of malware or attackers.
- **Spyware/Adware** – Collects user data without consent.
- **Botnets** – Network of compromised devices under remote control.

Common analysis tools: **Ghidra**, **IDA Pro**, **Wireshark**, **Cuckoo Sandbox**.

---

_That wraps up all the key questions from my evaluation day! Hope this post helps others prepping for cyber security interviews. Let me know if you'd like me to break down any of these topics further or add diagrams/code examples._

---
