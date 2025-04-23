---
title: "System Boot, Startup, and Shutdown: Key Forensic Artifacts"
date: 2024-11-19  
categories: [DFIR]  
tags: [DFIR, System Boot, Startup, Shutdown, Forensics]  
author: Harmehar Kaur  
image:  
  path: /assets/attack.jpg  
  alt: System Boot and Shutdown Artifacts  
---

In today’s blog, we’re diving into **System Boot**, **Startup Programs**, and **Shutdown** artifacts in Windows, all of which are crucial in any **DFIR** investigation.

---

### System Boot and Auto-Start Programs

**System Boot programs** are applications that run when the system boots up. Additionally, **auto-start programs** are those that run when a user logs on. These programs are often of interest when investigating **malware**, or simply auditing **installed software**.

Here are some important locations to check for these artifacts:

- `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`
- `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`
- `SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`
- `SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run`
- `SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
- `SYSTEM\CurrentControlSet\Services`

If the **Start** value is set to **0x02**, the service application will start during boot, while **0x00** indicates a driver.

**Why is this important?**  
These artifacts can be incredibly helpful in detecting **malware** or investigating what programs are set to run at startup. It’s worth noting that this is not an exhaustive list of autorun locations, but it provides a solid foundation for your investigation.

---

### System Last Shutdown Time

Windows stores the **last shutdown time** of the system, which can be an important piece of evidence during investigations. In **Windows XP**, it even tracks the number of times the system has been shut down.

This information can be helpful in determining the last activity on the system and spotting any **user behavior anomalies**.

These shutdown artifacts can be found at:

- `SYSTEM\CurrentControlSet\Control\Windows` (Shutdown Time)
- `SYSTEM\CurrentControlSet\Control\Watchdog\Display` (Shutdown Count – WinXP only)

The **Shutdown Time** is stored in the **Windows 64-bit FILETIME format**, making it an excellent source for determining the last system shutdown.

---

### Key Takeaways

- Boot and auto-start programs help investigators determine which applications are set to launch at startup.
- System shutdown artifacts provide insight into when the system was last used and can assist in building timelines.
- These artifacts are crucial for uncovering potential **malware**, **user activity**, or **system anomalies**.

Stay tuned for more posts on **Windows forensics** and how these artifacts help in **digital forensics investigations**!
