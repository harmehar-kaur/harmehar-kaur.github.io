---
title: Understanding Windows Registry Artifacts in DFIR  
date: 2024-11-07  
categories: [DFIR]  
tags: [DFIR, Windows Registry, Registry Artifacts, Digital Forensics, Incident Response]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Windows Registry Artifacts  
---

Now that I’ve found my interest in DFIR (Digital Forensics and Incident Response), I’m diving deeper into some of the core concepts—starting with Windows system artifacts.

Today’s topic of interest is **registry artifacts**.

---

### What is the Windows Registry?

The Windows Registry is essentially a collection of databases that store configuration information in key-value pairs. These details could relate to hardware, software, or user-specific information such as:

- The current user
- Recently opened files
- Programs accessed
- Devices connected

You can view and edit the registry on a live system using the `regedit.exe` utility. It gives you access to the registry in a graphical interface, but remember—this only works on a live system.

---

### Registry Hives

Windows has **five main registry hives**, which are essentially collections of keys, subkeys, and values stored on disk. These hives are frequently analyzed during forensic investigations, especially since live access isn’t always possible.

These are the five hives:

- **DEFAULT**  
- **SAM**  
- **SECURITY**  
- **SOFTWARE**  
- **SYSTEM**  

You’ll find them stored at:  
`C:\Windows\System32\Config`

#### SAM Hive

The **SAM (Security Account Manager)** hive contains information related to user accounts, login credentials, and group memberships. You’ll usually find this data under:  
`SAM\Domains\Account\User`

---

### Registry Keys

The registry is organized into **root keys** that act as entry points to different parts of the system’s configuration data. Here are the main ones:

- **HKEY_CURRENT_USER**: A subkey of `HKEY_USERS`, it holds config info specific to the current user.
- **HKEY_USERS**: Contains all loaded user profiles.
- **HKEY_LOCAL_MACHINE**: Stores config data relevant to the entire computer.
- **HKEY_CLASSES_ROOT**: A subkey of `HKEY_LOCAL_MACHINE`, this one deals with information about currently opened programs via Windows Explorer.
- **HKEY_CURRENT_CONFIG**: Reflects the hardware profile currently being used by the local machine.

---

### Registry Transaction Logs and Backups

There are also **transaction logs** and **backups** associated with the registry.

- **Transaction logs** (`.log` files) are changelogs for the registry hives. These are more up-to-date than the hive files themselves, capturing recent activity that hasn’t yet been committed to the hive.
  
- **Backups**, in contrast, reflect older states of the registry. The registry hives in the config directory are backed up every ten days and stored at:  
  `C:\Windows\System32\Config\RegBack`

---

That wraps up today’s dive into registry artifacts. There’s so much to explore in DFIR, and understanding these low-level system components is key to building a solid foundation.

Stay tuned as I continue this learning journey—next up, more Windows artifacts!
