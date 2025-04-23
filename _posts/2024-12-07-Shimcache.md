---
title: Understanding ShimCache in DFIR  
date: 2024-12-07  
categories: [DFIR]  
tags: [DFIR, Forensics, ShimCache, AppCompatCache, Windows, Artifacts]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: ShimCache Artifact  
---

In **Digital Forensics and Incident Response (DFIR)**, the **ShimCache** artifact, also known as the **Application Compatibility Cache** or **AppCompatCache**, plays an important role in tracking applications launched on a Windows machine. While it's typically associated with backward compatibility, it has become a crucial piece of evidence when investigating system activity.

---

### What Is ShimCache?

The **ShimCache** is a mechanism that helps ensure application compatibility with the operating system. It tracks information about every application launched on the system, including the executable file name, file path, and the last modification time of the file. In simple terms, it helps ensure that older applications can run smoothly on newer versions of Windows.

However, **ShimCache** is not necessarily evidence of **execution** on **Windows 10** or later. While it was once considered an indicator of execution, it is now primarily evidence of the **presence** of an application. It retains the last 1024 entries and is updated only when the system is rebooted or shut down. 

It's important to note that **renaming or moving a file** will cause it to be re-shimmed, which means the information in ShimCache will be updated accordingly.

---

### Key Information in ShimCache

The **ShimCache** records several important details about each application launched, including:

- **Executable File Name**
- **File Path**
- **Timestamp**: The last modification time of the file
- **File Size**: The size of the file
- **Executables**: Information about executable files that were run on the system

---

### Where Is ShimCache Stored?

The **ShimCache** is stored in the **SYSTEM** hive of the Windows Registry. Specifically, you can find it at:

- **SYSTEM\CurrentControlSet\Control\SessionManager\AppCompatCache**

This location in the registry allows forensic investigators to access the **ShimCache** data for analysis. With the help of tools like **AppCompatParser** (a tool developed by Zimmerman), investigators can easily parse the **ShimCache** and output the data into a **CSV** file for further analysis.

---

### How Can ShimCache Help in DFIR Investigations?

In **DFIR**, the **ShimCache** provides vital information about applications that have been launched on a system. Here are a few ways it can be helpful:

- **Evidence of Presence**: It can confirm that an application has been run on a system, even if no trace of its execution is found in other logs or artifacts.
- **Tracking Suspicious Activity**: By analyzing the executables listed in **ShimCache**, investigators can identify potentially suspicious applications that were run or accessed on the system.
- **Time Analysis**: The timestamps recorded in **ShimCache** can be useful for building timelines of system activity, helping investigators determine when specific applications were launched.

---

### Conclusion

While **ShimCache** is no longer considered evidence of execution on **Windows 10** or later, it remains a valuable artifact for **DFIR** investigations. By tracking application launches, it helps forensic experts confirm the presence of programs on a system, offering insights into potential user activity or malicious actions. The **ShimCache** also aids in identifying suspicious programs and assists in timeline reconstruction. 

So, whether you’re investigating an incident or conducting a routine review of a system, **ShimCache** should definitely be on your list of artifacts to check.

