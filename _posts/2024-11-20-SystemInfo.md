---
title: Understanding System Configuration Artifacts in DFIR  
date: 2024-11-20  
categories: [DFIR]  
tags: [DFIR, System Configuration, Forensics, Windows]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: System Configuration Artifacts  
---

When diving into **DFIR (Digital Forensics and Incident Response)**, understanding system configuration artifacts is key to piecing together evidence about a machine’s setup and usage. These artifacts help us understand not just how a system is configured, but also how it operates at a deeper level. Let's break down some important **system configuration artifacts** you should know.

---

### OS Version

The **OS version** provides a snapshot of the operating system running on the machine. This can help investigators determine what version of Windows the system is using, which is critical when looking for specific vulnerabilities or artifacts related to that version.

- **Location**:  
  - `SOFTWARE\Microsoft\Windows NT\CurrentVersion`

---

### Control Sets

**Control Sets** are registry hives that store configuration data essential for system startup. Typically, there are two **Control Sets** that are present:

1. **ControlSet001** – This is typically the control set used to boot the machine.
2. **ControlSet002** – Stores the last known good configuration.

In addition to these, there's a **volatile control set** called **CurrentControlSet**, which is used to get the most current system information when working with a live system. 

- **Location**:  
  - `SYSTEM\Select\Current`  
- **Last Known Good Configuration**:  
  - `SYSTEM\Select\LastKnownGood`

---

### Computer Name

The **computer name** is essential for ensuring you're working with the correct machine during an investigation. It’s especially useful for identifying systems when working with a network of machines or when there are multiple machines involved in a case.

- **Location**:  
  - `SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`

---

### Time Zone Information

Time zone data helps correlate timestamps across various files and media. This is crucial when building a **timeline** of events or understanding when certain actions were performed on the system.

- **Location**:  
  - `SYSTEM\CurrentControlSet\Control\TimeZone\Information`

---

### Network Interfaces

Network interfaces and the records of past networks can be incredibly useful for identifying IP addresses, DNS servers, DHCP IP addresses, subnet masks, and more. This can give you a clear picture of the machine’s network activity.

- **Location**:  
  - `SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces`  
  - `SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signature\Unmanaged`  
  - `SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signature\Managed`

---

### Key Takeaways

- **System Configuration Artifacts** provide vital information about the setup of a machine, helping investigators understand its structure and how it has been used.
- Locations like **ControlSets**, **Computer Name**, and **Network Interfaces** provide critical data that can tie events together or identify the system in question.
- Time zone and network interface data play crucial roles in analyzing system activity and correlating timestamps with events.

---

This is just the tip of the iceberg when it comes to system configuration in **DFIR**. Keep these artifacts in mind when analyzing a Windows system, as they can reveal a wealth of information about how the system operates and when certain activities occurred.

Stay tuned for more DFIR tips and insights in upcoming posts!
