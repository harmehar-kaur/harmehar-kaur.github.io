---
title: "Part 6 - Understanding MITRE ATT&CK Framework: Privilege Escalation"
date: 2025-01-16
categories: [MITRE]
tags: [ATT&CK, cybersecurity, adversary tactics, techniques, MITRE]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: MITRE ATT&CK framework
---

## Introduction

In this post, we’re diving into the **Privilege Escalation** tactic within the MITRE ATT&CK framework. Adversaries use these techniques to gain higher-level permissions, such as SYSTEM/root access or local administrator rights, often after initially entering a system with limited user privileges.

Privilege Escalation is commonly achieved by exploiting system vulnerabilities, misconfigurations, or weaknesses in access controls—and frequently overlaps with **persistence** techniques.

Let’s walk through the key techniques and their sub-techniques used by attackers to escalate their privileges.

---

## Techniques and Sub-techniques

### 1. **Abuse Elevation Control Mechanism (T1548)**
Methods that circumvent built-in system mechanisms intended to prevent unauthorized privilege elevation.
- `.001` Setuid and Setgid
- `.002` Bypass User Account Control
- `.003` Sudo and Sudo Caching
- `.004` Elevated Execution with Prompt
- `.005` Temporary Elevated Cloud Access
- `.006` TCC Manipulation

---

### 2. **Access Token Manipulation (T1134)**
Attackers manipulate access tokens to operate as different users or processes.
- `.001` Token Impersonation/Theft
- `.002` Create Process with Token
- `.003` Make and Impersonate Token
- `.004` Parent PID Spoofing
- `.005` SID-History Injection

---

### 3. **Account Manipulation (T1098)**
Changing or abusing user accounts to elevate privileges.
- `.001` Additional Cloud Credentials
- `.002` Additional Email Delegate Permissions
- `.003` Additional Cloud Roles
- `.004` SSH Authorized Keys
- `.005` Device Registration
- `.006` Additional Container Cluster Roles
- `.007` Additional Local or Domain Groups

---

### 4. **Boot or Logon Autostart Execution (T1547)**
Configuring programs to execute during system boot or user logon.
- `.001` Registry Run Keys / Startup Folder
- `.002` Authentication Package
- `.003` Time Providers
- `.004` Winlogon Helper DLL
- `.005` Security Support Provider
- `.006` Kernel Modules and Extensions
- `.007` Re-opened Applications
- `.008` LSASS Driver
- `.009` Shortcut Modification
- `.010` Port Monitors
- `.012` Print Processors
- `.013` XDG Autostart Entries
- `.014` Active Setup
- `.015` Login Items

---

### 5. **Boot or Logon Initialization Scripts (T1037)**
Using scripts that execute at boot/logon for privilege escalation or persistence.
- `.001` Logon Script (Windows)
- `.002` Login Hook
- `.003` Network Logon Script
- `.004` RC Scripts
- `.005` Startup Items

---

### 6. **Create or Modify System Process (T1543)**
Creating or modifying services or daemons to run adversary-controlled code.
- `.001` Launch Agent
- `.002` Systemd Service
- `.003` Windows Service
- `.004` Launch Daemon
- `.005` Container Service

---

### 7. **Domain or Tenant Policy Modification (T1484)**
Changing domain/tenant-wide policies to elevate access.
- `.001` Group Policy Modification
- `.002` Trust Modification

---

### 8. **Escape to Host (T1611)**
Breaking out of a container or virtual machine to access the host OS.

---

### 9. **Event Triggered Execution (T1546)**
Using system event triggers to execute code with elevated privileges.
- `.001` Change Default File Association
- `.002` Screensaver
- `.003` WMI Event Subscription
- `.004` Unix Shell Configuration Modification
- `.005` Trap
- `.006` LC_LOAD_DYLIB Addition
- `.007` Netsh Helper DLL
- `.008` Accessibility Features
- `.009` AppCert DLLs
- `.010` AppInit DLLs
- `.011` Application Shimming
- `.012` Image File Execution Options Injection
- `.013` PowerShell Profile
- `.014` Emond
- `.015` Component Object Model Hijacking
- `.016` Installer Packages
- `.017` Udev Rules

---

### 10. **Exploitation for Privilege Escalation (T1068)**
Exploiting software vulnerabilities to run code with elevated permissions.

---

### 11. **Hijack Execution Flow (T1574)**
Redirecting normal execution flow to run attacker-supplied code.
- `.001` DLL Search Order Hijacking
- `.004` Dylib Hijacking
- `.005` Executable Installer File Permissions Weakness
- `.006` Dynamic Linker Hijacking
- `.007` Path Interception by PATH Environment Variable
- `.008` Path Interception by Search Order Hijacking
- `.009` Path Interception by Unquoted Path
- `.010` Services File Permissions Weakness
- `.011` Services Registry Permissions Weakness
- `.012` COR_PROFILER
- `.013` KernelCallbackTable
- `.014` AppDomainManager

---

### 12. **Process Injection (T1055)**
Injecting malicious code into legitimate processes.
- `.001` DLL Injection
- `.002` PE Injection
- `.003` Thread Execution Hijacking
- `.004` Asynchronous Procedure Call
- `.005` Thread Local Storage
- `.008` Ptrace System Calls
- `.009` Proc Memory
- `.011` Extra Window Memory Injection
- `.012` Process Hollowing
- `.013` Process Doppelgänging
- `.014` VDSO Hijacking
- `.015` ListPlanting

---

### 13. **Scheduled Task/Job (T1053)**
Abusing scheduling utilities to execute code repeatedly with elevated privileges.
- `.002` At
- `.003` Cron
- `.005` Scheduled Task
- `.006` Systemd Timers
- `.007` Container Orchestration Job

---

### 14. **Valid Accounts (T1078)**
Using legitimate account credentials to gain higher access.
- `.001` Default Accounts
- `.002` Domain Accounts
- `.003` Local Accounts
- `.004` Cloud Accounts

---

## Conclusion

Privilege escalation is a crucial step in most attacks, enabling adversaries to take full control of compromised systems. Understanding these techniques and their sub-techniques is key to building effective detection and prevention strategies.

Stay tuned for the next post in the series, where we’ll explore the **Defense Evasion** tactic.

