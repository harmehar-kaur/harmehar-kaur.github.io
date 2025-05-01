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
- Setuid and Setgid
- Bypass User Account Control
- Sudo and Sudo Caching
- Elevated Execution with Prompt
- Temporary Elevated Cloud Access
- TCC Manipulation

---

### 2. **Access Token Manipulation **
Windows use access tolen to determine the ownership of running processes and attackers manipulate access tokens to operate as different users or processes. Copying tokens from the existing processes could be used in token impersonation/theft and creating new process with tokens. In windows any user can use runas to impersonate tokens. active directory fields could also be used to modify access tokens. mitigation of this technique is done by proper management of user as well as privileged accounts. the traces left behind could be detected if there is presence of active directory object modification, command execution OS API execution, process creation, and user account metadata.  
- Token Impersonation/Theft
- Create Process with Token
- Make and impersonate token
- Parent PID spoofing 
- SID history injection 

---

### 3. **Account Manipulation (T1098)**
Changing or abusing user accounts to elevate privileges.
- Additional Cloud Credentials
- Additional Email Delegate Permissions
- Additional Cloud Roles
- SSH Authorized Keys
- Device Registration
- Additional Container Cluster Roles
- Additional Local or Domain Groups

---

### 4. **Boot or Logon Autostart Execution (T1547)**
Configuring programs to execute during system boot or user logon.
- Registry Run Keys / Startup Folder
- Authentication Package
- Time Providers
- Winlogon Helper DLL
- Security Support Provider
- Kernel Modules and Extensions
- Re-opened Applications
- LSASS Driver
- Shortcut Modification
- Port Monitors
- Print Processors
- XDG Autostart Entries
- Active Setup
- Login Items

---

### 5. **Boot or Logon Initialization Scripts (T1037)**
Using scripts that execute at boot/logon for privilege escalation or persistence.
- Logon Script (Windows)
- Login Hook
- Network Logon Script
- RC Scripts
- Startup Items

---

### 6. **Create or Modify System Process (T1543)**
Creating or modifying services or daemons to run adversary-controlled code.
- Launch Agent
- Systemd Service
- Windows Service
- Launch Daemon
- Container Service

---

### 7. **Domain or Tenant Policy Modification (T1484)**
Changing domain/tenant-wide policies to elevate access.
- Group Policy Modification
- Trust Modification

---

### 8. **Escape to Host (T1611)**
Breaking out of a container or virtual machine to access the host OS.

---

### 9. **Event Triggered Execution (T1546)**
Using system event triggers to execute code with elevated privileges.
- Change Default File Association
- Screensaver
- WMI Event Subscription
- Unix Shell Configuration Modification
- Trap
- LC_LOAD_DYLIB Addition
- Netsh Helper DLL
- Accessibility Features
- AppCert DLLs
- AppInit DLLs
- Application Shimming
- Image File Execution Options Injection
- PowerShell Profile
- Emond
- Component Object Model Hijacking
- Installer Packages
- Udev Rules

---

### 10. **Exploitation for Privilege Escalation (T1068)**
Exploiting software vulnerabilities to run code with elevated permissions.

---

### 11. **Hijack Execution Flow (T1574)**
Redirecting normal execution flow to run attacker-supplied code.
- DLL Search Order Hijacking
- Dylib Hijacking
- Executable Installer File Permissions Weakness
- Dynamic Linker Hijacking
- Path Interception by PATH Environment Variable
- Path Interception by Search Order Hijacking
- Path Interception by Unquoted Path
- Services File Permissions Weakness
- Services Registry Permissions Weakness
- COR_PROFILER
- KernelCallbackTable
- AppDomainManager

---

### 12. **Process Injection**
This is when adversary executes arbitary code in the address space of another live process which allows access to process's memory, system or network resources, and elevated privileges. this evades detection since is running under a legitimate process. these could be mitigated by managing the privileged account management and behaviour prevention or endpoint. the detection of these could be done using information like file metadata, file modification, module load, OS API execution, process access, process metadata and process modification.  
Injecting malicious code into legitimate processes.
- DLL Injection
- PE Injection
- Thread Execution Hijacking
- Asynchronous Procedure Call
- Thread Local Storage
- Ptrace System Calls
- Proc Memory
- Extra Window Memory Injection
- Process Hollowing
- Process Doppelgänging
- VDSO Hijacking
- ListPlanting

---

### 13. **Scheduled Task/Job (T1053)**
Abusing scheduling utilities to execute code repeatedly with elevated privileges.
- At
- Cron
- Scheduled Task
- Systemd Timers
- Container Orchestration Job

---

### 14. **Valid Accounts (T1078)**
Using legitimate account credentials to gain higher access.
- Default Accounts
- Domain Accounts
- Local Accounts
- Cloud Accounts

---

## Conclusion

Privilege escalation is a crucial step in most attacks, enabling adversaries to take full control of compromised systems. Understanding these techniques and their sub-techniques is key to building effective detection and prevention strategies.

Stay tuned for the next post in the series, where we’ll explore the **Defense Evasion** tactic.

