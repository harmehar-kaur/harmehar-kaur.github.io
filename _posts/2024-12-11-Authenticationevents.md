---
title: "Authentication Events in DFIR: Tracking Credentials and Account Usage"  
date: 2024-12-11  
categories: [DFIR]  
tags: [DFIR, Authentication, Event Logs, Windows, Credentials, NTLM, Kerberos]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Authentication Event Logs  
---

When it comes to **Digital Forensics and Incident Response (DFIR)**, understanding **authentication events** is essential for tracking the usage of local and domain accounts. These events tell investigators where and when credentials were authenticated, providing insight into account activity and potentially pointing to suspicious behavior.

---

### What Are Authentication Events?

Authentication events record actions where credentials (like usernames and passwords) are verified on a system. These logs help track both **local account** activity (e.g., on individual workstations) and **domain account** activity (e.g., on domain controllers).

Authentication events are stored in different locations depending on the type of account being used:

- **Local Account/Workgroup**: The events are recorded on the workstation where the credentials are authenticated.
- **Domain/Active Directory**: The events are recorded on the domain controller.

This makes it crucial to know where the records are stored in order to track account usage accurately.

---

### Location of Authentication Event Logs

These events are logged on the system where the credentials are authenticated, and they can be found in the following location:

- **Location**:  
  `Win7+: %SYSTEMROOT%\System32\winevt\logs\Security.evtx`

This log is a key source of information when investigating authentication attempts, helping investigators track the usage of credentials across different systems.

---

### Key Event ID Codes

The event logs capture various actions related to authentication. These include both **NTLM** and **Kerberos** protocol events:

- **NTLM Protocol Event IDs**:
  - **4776**: Successful or failed account authentication using NTLM.
  
- **Kerberos Protocol Event IDs**:
  - **4768**: A Ticket Granting Ticket (TGT) was granted (successful logon).
  - **4769**: Service Ticket requested (access to a server resource).
  - **4771**: Pre-authentication failed (failed logon attempt).

Each of these events provides valuable information for investigators, helping them to differentiate between successful and failed authentication attempts, and trace the activity to the associated account.

---

### Why Are Authentication Events Important?

Authentication events are essential for any DFIR investigation because they provide clear evidence of who accessed a system, when they accessed it, and whether the authentication was successful. By analyzing these logs, investigators can:

- Track **local** versus **domain** account usage.
- Identify potential **failed logins** or suspicious authentication attempts.
- Correlate these events with other activities on the system, helping to piece together a timeline of events.
- Identify **successful logins** or attempts to escalate privileges, indicating possible unauthorized access.

---

### Conclusion

Authentication events are an important source of information for tracking and analyzing user behavior within a system. By reviewing these logs, investigators can uncover critical details about account usage, authentication methods, and any potentially malicious activity tied to credential access.

---
