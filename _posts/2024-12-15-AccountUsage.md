---
title: Understanding Account Usage in DFIR  
date: 2024-12-15  
categories: [DFIR]  
tags: [DFIR, Account Usage, Microsoft Cloud, User Access Logging, Forensics]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Account Usage in DFIR  
---

When investigating **Digital Forensics and Incident Response (DFIR)**, tracking **account usage** can provide critical insights into user activity, especially when dealing with cloud-based accounts and user access logs. Let’s dive into the various sources where this information is stored and how it can be used during an investigation.

---

### Cloud Account Details

Microsoft Cloud accounts store crucial account information in the **SAM (Security Account Manager)** hive. This includes the email address tied to the cloud account, which helps in identifying whether the account is a Microsoft cloud account.

- **Location**:  
  - `SAM\Domains\Account\Users\<InternetUserName>`  
    - The `InternetUserName` value contains the email address associated with the account. The presence of this value indicates the account is a Microsoft cloud account.

---

### Last Login and Password Change

The **SAM registry hive** keeps track of local accounts and configuration details such as the last login time, password changes, login counts, group memberships, and account creation times.

- **Location**:  
  - `SAM\Domains\Account\Users`  
    - Accounts are listed by their **Relative Identifiers (RIDs)**, and you can extract critical information like login time and password change history.

---

### User Access Logging

Introduced in **Windows Server 2012** and later, **User Access Logging (UAL)** is an essential feature for tracking user access and system-related data in near real-time. It’s particularly useful in identifying abnormal access patterns, profiling lateral movements, and understanding how users are interacting with systems.

- **Location**:  
  - `C:\Windows\System32\LogFiles\SUM\`  
    - This directory contains files such as `SystemIdentity.mdb`, `Current.mdb`, and other GUID-based files.  
    - The **UAL database** tracks active user and system activity data, including the source IP address, role, and UTC timestamps for both first and last access.

The system retains data for the current year, the previous year, and up to two years prior, while archived events are stored for 24 hours. This allows for efficient tracking of user access patterns and potential suspicious activity across multiple systems.

---

### Key Insights from User Access Logs

- **IP Tracking**: The system records the source IP address from which activity originates, helping investigators pinpoint abnormal access points.  
- **Profile Lateral Movement**: UAL logs are especially valuable in tracking lateral movement from clients to servers, revealing unauthorized access attempts or unauthorized privilege escalation.
- **Access Timestamps**: The UTC timestamps (InsertDate and LastAccess) provide a precise timeline of when access occurred.

User Access Logging is especially helpful for administrators in understanding the overall usage of services on a server. It details which usernames were involved, the services accessed, and the source IP addresses, providing an extensive view of server interactions.

---

By understanding where and how account usage data is stored, you can uncover valuable insights into user activity, login attempts, and potential security incidents. Always remember to check both local and cloud-based sources to gather a comprehensive view of what’s happening on your systems.

---
