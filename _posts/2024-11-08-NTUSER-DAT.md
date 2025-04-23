---
title: Exploring the NTUSER.DAT Hive in Windows Forensics  
date: 2024-11-08  
categories: [DFIR]  
tags: [DFIR, NTUSER.DAT, Windows Registry, User Artifacts, Digital Forensics]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: NTUSER.DAT Registry Hive  
---

Let’s talk about one of the most interesting and user-specific registry artifacts in Windows: **NTUSER.DAT**.

---

### What is NTUSER.DAT?

The `NTUSER.DAT` file is a **registry hive** that stores configuration settings and preferences for a specific user. Every time a user logs into Windows and interacts with files, programs, or system features, those interactions are reflected here in some way.

This hive can contain a wealth of information, such as:

- User preferences
- Recently accessed files
- Application usage history
- Shell settings and more

In forensic investigations, `NTUSER.DAT` is a goldmine for reconstructing user activity on a system.

---

### Where is it located?

You’ll find this file in the user’s profile directory:

`C:\Users<Username>\NTUSER.DAT`


Each user on the system will have their own `NTUSER.DAT` file, which makes it incredibly useful for attributing actions to specific accounts.

---

This file plays a crucial role in user-level analysis during DFIR investigations. So if you're digging into what a user was up to on a machine, this is definitely a place you’ll want to look.

More artifact breakdowns coming soon!
