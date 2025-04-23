---
title: "Recent Files and Documents: A Forensic Insight"
date: 2024-11-23  
categories: [DFIR]  
tags: [DFIR, Forensics, Windows, Recent Files]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Recent Files Forensic Analysis  
---

When investigating a Windows system, understanding how **recently opened files** and **documents** are tracked is key to piecing together a timeline of user activity. **Windows** stores information about files that users have recently accessed, and this data can be crucial in uncovering what was being worked on during a specific time.

Let’s dive into where this data is stored and how it can be used in a **DFIR** investigation.

---

### Recent Files and Documents Tracking in Windows

Windows not only tracks the applications that were opened but also stores detailed information about files accessed by users. This information is primarily stored in the **NTUSER hive**. Here are some key locations where Windows keeps track of recently opened files:

- **Location**:  
  - `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\<file_extension>`  
    *(e.g., .pdf, .jpg, etc. – any file extension you're interested in)*

In addition to the standard file extensions, **Microsoft Office** also maintains a list of recently opened documents:

- **Location for Microsoft Office (pre-365)**:  
  - `NTUSER.DAT\Software\Microsoft\Office\<Version>\`

For users with **Microsoft 365**, the tracking is tied to their **Live ID**:

- **Location for Microsoft 365**:  
  - `NTUSER.DAT\Software\Microsoft\Office\<Version>\UserMRU\LiveID_####\FileMRU`

This ensures that even when users are logged in across different devices, their recent documents can be tracked as part of their user profile.

---

### Why Does This Matter in Forensics?

These entries can be extremely useful when performing a forensic investigation. By examining the **RecentDocs** and **Office MRU** locations, you can:

- Identify files that were recently accessed by the user.
- Correlate file access with specific events or actions on the system.
- Investigate the activity of specific users, especially in environments where user activity needs to be tracked over time.

These artifacts offer a wealth of information that can help establish a **timeline of events** or uncover unauthorized access to sensitive files.

---

### Conclusion

In DFIR, understanding how Windows tracks recently opened files and documents is crucial. By exploring the relevant registry locations, forensic investigators can uncover valuable insights into user activity, file access patterns, and even potential malicious behavior. 

Make sure to check the **NTUSER hive** and other related locations to piece together the puzzle when analyzing Windows systems.

Stay tuned for more posts on how to utilize Windows artifacts in DFIR investigations!
