---
title: Logon Event Types and Service Events in DFIR  
date: 2024-12-12  
categories: [DFIR]  
tags: [DFIR, Logon Events, Windows, Event Logs, Security, Malware, Persistence]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Logon Event Logs  
---

When diving into **Digital Forensics and Incident Response (DFIR)**, one of the key areas to explore is **logon events**. These events provide crucial insights into how accounts are being accessed, by whom, and from where. They offer an in-depth view of user activity, helping investigators track any unusual logon patterns that may indicate suspicious activity.

---

### Understanding Logon Event Types

Logon events capture a range of details about **account authorizations** on a system. These events record when a user attempts to log on, providing essential information such as:

- **Date and Time** of logon
- **Username**
- **Hostname**
- **Success or failure** of the logon attempt
- The **method** used for the logon

This information can help an investigator understand the context of a logon attempt, whether it’s legitimate or potentially malicious.

---

### Location of Logon Event Logs

The logon events are stored in the **Security.evtx** file, which can be found in the following location:

- **Location**:  
  `Win7+: %SYSTEMROOT%\System32\winevt\logs\Security.evtx`

---

### Event ID 4624: Understanding Different Logon Types

**Event ID 4624** records successful logons, and it provides important context for the logon attempt, including the logon type. Here’s a breakdown of the logon types you may encounter:

- **Type 2**: Logon via console
- **Type 3**: Network logon
- **Type 4**: Batch logon
- **Type 5**: Windows service logon
- **Type 7**: Credentials used to unlock screen; RDP session reconnect
- **Type 8**: Network logon sending credentials (cleartext)
- **Type 9**: Different credentials used than logged-on user
- **Type 10**: Remote interactive logon
- **Type 11**: Cache credentials used to log on
- **Type 12**: Cached remote interactive (similar to Type 10)
- **Type 13**: Cached unlock (similar to Type 7)

Each type tells you the nature of the logon attempt, whether it was via a direct console, network access, or even cached credentials.

---

### Successful and Failed Logons

Windows also keeps track of successful and failed logon attempts. This information is essential in identifying unauthorized access attempts or any irregularities in account usage. You’ll find these events recorded as:

- **4624**: Successful logon
- **4625**: Failed logon
- **4634**: Successful logoff
- **4647**: Logoff initiated by the user
- **4648**: Logon using explicit credentials (runas)
- **4672**: Account logon with superuser rights (admin privileges)
- **4720**: An account was created

These events help provide a clear picture of account activity, highlighting both successful access and potential failed attempts.

---

### Service Events and Malware Persistence

**Service events** are another crucial area to explore when investigating suspicious activity. Windows services play a key role in malware persistence—many malware strains leverage services to maintain access to a compromised system. These events can help identify unusual or unauthorized services being installed, started, or stopped.

Here’s a list of relevant service events you should look for:

- **7034**: Service crashed unexpectedly
- **7035**: Service sent a Start/Stop control
- **7036**: Service started or stopped
- **7040**: Start type changed (Boot | On Request | Disabled)
- **7045**: A service was installed on the system (Win2008R2+)
- **4697**: A service was installed on the system (from Security log in Win10+)

Investigators should pay particular attention to services that are started on boot or those that persist across reboots—these could indicate malware leveraging Windows services for continued access.

---

### Conclusion

Understanding **logon events** and **service events** is essential for tracking user behavior and detecting potential unauthorized activity. By analyzing these event logs, investigators can build timelines, identify malicious actions, and gain critical insight into the security state of a system. Whether it's tracking **failed logons** or identifying **persistent malware** via services, these logs are invaluable tools in a DFIR investigation.

---
