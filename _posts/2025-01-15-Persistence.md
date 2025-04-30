---
title: "Part 5 - Understanding MITRE ATT&CK Framework: Persistence"
date: 2025-01-12
categories: [MITRE]
tags: [ATT&CK, cybersecurity, adversary tactics, techniques, MITRE]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: MITRE ATT&CK framework
---

## Introduction

In this part of our series, we're diving into the **Persistence** tactic within the MITRE ATT&CK framework. Persistence techniques are methods adversaries use to maintain their foothold on systems, even after restarts, credential changes, or other interruptions. These techniques ensure that attackers can return to compromised systems whenever they choose.

Let's explore the various techniques adversaries employ to achieve persistence.

---

## 1. Account Manipulation

Adversaries may manipulate accounts to maintain access to victim systems. This includes actions like:

- **Adding or modifying credentials**: Changing passwords or adding new credentials to existing accounts.
- **Assigning additional roles or permissions**: Granting elevated privileges to accounts.
- **Modifying authentication mechanisms**: Altering how authentication is handled to favor the attacker.

Sub-techniques include:

- Additional Cloud Credentials
- Additional Cloud Roles
- Additional Email Delegate Permissions
- Additional Local or Domain Groups
- SSH Authorized Keys
- Device Registration
- Additional Container Cluster Roles

---

## 2. BITS Jobs

The **Background Intelligent Transfer Service (BITS)** is a component of Microsoft Windows that facilitates asynchronous, prioritized, and throttled transfer of files between machines using idle network bandwidth. Adversaries can abuse BITS to create jobs that execute malicious programs.

---

## 3. Boot or Logon Autostart Execution

Attackers configure system settings to automatically execute programs during system boot or user logon. Methods include:

- **Registry Run Keys / Startup Folder**: Adding entries to the registry or startup folder to launch programs.
- **Authentication Package**: Installing custom authentication packages.
- **Time Providers**: Registering malicious DLLs as time providers.
- **Logon Scripts**: Setting scripts to run at logon.
- **Security Support Provider (SSP)**: Adding malicious SSPs.
- **Print Processors**: Installing malicious print processors.
- **Shortcut Modification**: Altering shortcuts to execute malicious code.
- **XDG Autostart Entries**: Creating autostart entries in Linux environments.

---

## 4. Boot or Logon Initialization Scripts

Adversaries use scripts that are executed during the boot or logon process to establish persistence. Examples include:

- **Logon Scripts**: Scripts set to run at user logon.
- **Login Hooks**: macOS-specific scripts that run at user login.
- **Startup Items**: Programs or scripts set to run at system startup.

---

## 5. Browser Extensions

Malicious browser extensions can be installed to maintain persistence within a user's browser. These extensions can:

- **Execute arbitrary code**: Run malicious scripts.
- **Harvest credentials**: Capture user input.
- **Redirect traffic**: Alter browser behavior to benefit the attacker.

---

## 6. Compromise Host Software Binary

Attackers may modify legitimate software binaries to include malicious code. This ensures that when the software is executed, the attacker's code runs as well.

---

## 7. Create Account

Creating new user accounts allows adversaries to maintain access. These accounts can be:

- **Local accounts**: Created on individual machines.
- **Domain accounts**: Created within an organization's domain.

---

## 8. Create or Modify System Process

Adversaries may create or modify system processes to execute malicious code. This includes:

- **Service Registry Permissions Weakness**: Exploiting weak permissions to modify services.
- **Launch Agent / Daemon**: Creating or modifying launch agents or daemons.
- **Systemd Service**: Creating or modifying systemd services in Linux.

---

## 9. Event Triggered Execution

Attackers set up mechanisms to execute code in response to specific events. Methods include:

- **Component Object Model (COM) Hijacking**: Redirecting COM object references.
- **Trap Signals**: Using signals to trigger code execution.
- **Unix Shell Configuration Modification**: Altering shell configurations to execute code.

---

## 10. External Remote Services

Adversaries may leverage external remote services to maintain access. This includes:

- **Remote Desktop Protocol (RDP)**: Using RDP to connect to systems.
- **Virtual Private Networks (VPNs)**: Establishing VPN connections to access networks.

---

## 11. Hijack Execution Flow

Attackers hijack the normal execution flow of applications to run their code. Techniques include:

- **DLL Search Order Hijacking**: Placing malicious DLLs in directories searched by applications.
- **DLL Side-Loading**: Placing malicious DLLs alongside legitimate applications.

---

## 12. Implant Internal Image

Adversaries implant malicious code into internal system images, ensuring that their code is present when systems are deployed or restored.

---

## 13. Modify Authentication Process

Attackers modify the authentication process to maintain access. This includes:

- **Password Filter DLLs**: Installing malicious DLLs that capture passwords.
- **Pluggable Authentication Modules (PAM)**: Modifying PAM configurations in Unix systems.

---

## 14. Modify Registry

In Windows systems, attackers modify the registry to achieve persistence. This includes:

- **Adding Run Keys**: Setting programs to run at startup.
- **Modifying Service Configurations**: Changing how services start.

---

## 15. Office Application Startup

Adversaries may abuse features in office applications to execute code. This includes:

- **Add-ins**: Installing malicious add-ins.
- **Macros**: Embedding malicious macros in documents.

---

## 16. Power Settings

Attackers modify power settings to prevent systems from sleeping or hibernating, ensuring their processes continue running.

---

## 17. Pre-OS Boot

Adversaries may execute code before the operating system boots. Techniques include:

- **Bootkits**: Malware that infects the master boot record (MBR).
- **UEFI/BIOS Firmware**: Modifying firmware to execute code.

---

## 18. Scheduled Task/Job

Creating scheduled tasks or jobs allows attackers to execute code at specific times or intervals. This includes:

- **Cron Jobs**: Scheduled tasks in Unix systems.
- **Scheduled Tasks**: Tasks scheduled in Windows Task Scheduler.

---

## 19. Server Software Component

Attackers may abuse server software components to maintain persistence. This includes:

- **Web Shells**: Placing malicious scripts on web servers.
- **Modules**: Installing malicious modules in server software.

---

## 20. Traffic Signaling

Adversaries may use network traffic patterns to signal malware to execute or perform actions. This includes:

- **Beaconing**: Regularly sending signals to a command and control server.
- **Protocol Manipulation**: Using specific protocols to trigger actions.

---

## 21. Valid Accounts

Using valid accounts, whether stolen or created, allows attackers to maintain access without triggering security alerts. This includes:

- **Default Accounts**: Exploiting default credentials.
- **Domain Accounts**: Using legitimate domain accounts.
- **Local Accounts**: Accessing systems with local user accounts.
- **Cloud Accounts**: Leveraging cloud service accounts.

---

Understanding these persistence techniques is crucial for defenders to detect and mitigate potential threats. By being aware of the methods adversaries use to maintain access, organizations can better secure their systems against prolonged attacks.
