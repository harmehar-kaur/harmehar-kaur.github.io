---
title: "UserAssist Keys: Tracking Program Launches in Windows" 
date: 2024-11-13  
categories: [DFIR]  
tags: [DFIR, UserAssist, Windows Registry, Execution Artifacts, User Activity]  
author: Harmehar Kaur  
image:  
  path: /assets/attack.jpg  
  alt: UserAssist Forensic Artifact  
---

Let’s look at another fascinating registry artifact that often flies under the radar: **UserAssist keys**.

---

### What is UserAssist?

UserAssist keys are part of the Windows registry that track **applications launched via Windows Explorer**. This includes programs opened from the Start menu, desktop shortcuts, or file explorer itself.

They’re like a hidden log of what the user has been running.

---

### Why is it useful in DFIR?

These keys don’t just record that an app was launched—they also capture:

- **How many times** it was executed  
- **When** it was last run  
- **Which program** was used  

That makes UserAssist keys extremely valuable for building a timeline of user activity on a system.

---

### Where can you find it?

You can locate these keys in the user's registry hive:
`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist{GUID}\Count`

The `{GUID}` changes depending on the system and version of Windows, but inside the `Count` subkey, you’ll find encoded entries that represent recently run applications and their metadata.

---

In short, if you’re trying to find out **what a user was running and how often**, UserAssist is a go-to artifact. It’s simple, subtle, and super effective for execution tracking.

Stick around—there’s more forensic goodness coming your way!
