---
title: "Detecting Incidents on Linux Disks: Key Forensic Surfaces" 
date: 2024-12-23  
categories: [DFIR]  
tags: [Linux Forensics, Disk Analysis, Incident Response, Filesystem Forensics, DFIR]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Linux Filesystem Forensics  
---

When an incident hits a Linux system, a deep dive into the disk can reveal a treasure trove of forensic evidence. These are the spots where attackers often leave traces—whether deliberately or inadvertently. In this post, we’ll break down key disk surfaces on a Linux machine that should be on your radar during forensic investigations.

---

### Overview

Linux disk surfaces refer to filesystem areas where traces of malicious activity may linger. From tampered config files to suspicious scripts hidden deep in system folders, each of these surfaces tells part of the story. Whether you’re investigating a breach or auditing for security posture, these are essential spots to examine.

---

### Key Disk Surfaces and Their Forensic Significance

#### Configuration Files

Attackers often tweak configuration files to create persistence, escalate privileges, or just avoid detection. These files should be reviewed closely:

- `/etc/passwd`  
  - Stores user account details (excluding passwords).
  - Key fields include: username, UID, GID, home directory, shell.

- `/etc/shadow`  
  - Contains hashed user passwords.
  - Restricted access makes it a target for brute-force and privilege escalation attacks.

- `/etc/group`  
  - Maps users to groups.
  - Check for unauthorized group memberships or the creation of suspicious groups.

- `/etc/sudoers`  
  - Governs sudo access.
  - Look for edits that provide attackers elevated privileges.

---

#### Investigating Installed Packages

If an attacker installs a malicious package, it often comes with scripts or executables designed to execute automatically.

- **List Installed Packages**  
  - Command: `dpkg -l`  
  - Scan the list for suspicious or out-of-place entries.

- **Check dpkg Logs**  
  - Log file location: `/var/log/dpkg.log`  
  - Use `grep " install " /var/log/dpkg.log` to filter recent installations for anything unusual.

---

#### Malicious Scripts in Package Installations

A package may appear legitimate but include scripts that run on install, often found within the package structure itself.

- **Package Metadata**  
  - Location: `DEBIAN/control` (inside the package)  
  - Check for odd descriptions, suspicious authors, or vague versioning.

- **Post-Installation Scripts**  
  - Location: `DEBIAN/postinst`  
  - These scripts execute automatically—inspect them for unexpected logic or actions.

- **File Permissions**  
  - Malicious actors might loosen file permissions to ease execution.  
  - Use `chmod` to check and correct access rights.

---

#### Key Directories

Certain directories are often abused by attackers for persistence or to hide scripts and tools.

- **System Services**  
  - Path: `/etc/systemd/system/`  
  - Look for services that don’t belong or launch processes not tied to the system’s core functions.

- **Cron Jobs**  
  - Path: `/var/spool/cron/`  
  - Cron jobs can silently execute malicious scripts at scheduled intervals.

- **Temporary Files**  
  - Path: `/tmp/`  
  - Temporary folders are easy to write to—often used to stage files or launch payloads.

---

Linux forensics isn’t just about logs and memory—it’s also about digging into the disk. These areas serve as the forensic equivalent of a crime scene, helping you reconstruct what happened, how, and hopefully, by whom. Always trust, but verify—especially when it comes to what’s hiding deep in your filesystems.
