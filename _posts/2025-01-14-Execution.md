---
title: "Part 4 - Understanding MITRE ATT&CK Framework: Execution"
date: 2025-01-14
categories: [MITRE]
tags: [ATT&CK, cybersecurity, adversary tactics, techniques, MITRE]
author: Harmehar Kaur
image:
  path: /assets/attack.jpg
  alt: MITRE ATT&CK framework
---

The **Execution** tactic includes techniques that result in **adversary-controlled code running** on a local or remote system. These techniques are often combined with others across the ATT&CK matrix to help adversaries achieve broader objectives like persistence, lateral movement, or impact.

Let’s explore some of the key ways attackers can get code running:

---

### 1. **Cloud Administration Command**

Attackers can abuse **cloud management services** to execute commands inside virtual machines. Tools like **AWS Systems Manager**, **Azure Runbooks**, or **Google Cloud Ops Agent** allow for **remote script execution** using pre-installed VM agents.

---

### 2. **Command and Scripting Interpreter**

This is one of the most common techniques where adversaries use built-in **command-line interfaces** or **scripting languages** to run commands and scripts. Examples include:
- **PowerShell** (Windows)
- **Windows Command Shell**
- **Unix/Linux Shells**
- **AppleScript**, **Python**, **JavaScript**
- **Visual Basic**, **AutoHotkey**, **Lua**
- **Network device CLI**, **CrowdStrike APIs**, and more

These interpreters give attackers powerful access to system functions.

---

### 3. **Container Administration Command**

If a system uses containers, attackers may leverage **container orchestration or admin tools** (like Docker Daemon or Kubernetes APIs) to run commands within those containers—especially if admin access is misconfigured or exposed.

---

### 4. **Deploy Container**

Instead of executing code on an existing machine, adversaries may **deploy their own container**, loaded with malware or preconfigured tasks. This container can help evade detection, bypass defenses, or act as a stepping stone to access other containers or resources—particularly in Kubernetes environments.

---

### 5. **Exploitation for Client Execution**

Attackers exploit **software vulnerabilities**—usually in client-side applications (like browsers, document viewers, or media players)—to force them to execute malicious code. These flaws typically result from insecure coding and can lead to unexpected behaviors.

---

### 6. **Inter-Process Communication (IPC)**

Attackers might abuse **IPC mechanisms**—used by processes to exchange data and coordinate operations—to execute code or manipulate running applications. Examples include:
- **Component Object Model (COM)**
- **Dynamic Data Exchange (DDE)**
- **XPC Services** on macOS

---

### 7. **Native API**

By interacting directly with **native operating system APIs**, adversaries can execute low-level operations involving hardware, memory, or services. These APIs offer more control and are often harder to detect when abused.

---

### 8. **Scheduled Jobs**

Attackers may create or modify **scheduled tasks** to trigger execution of malicious code. They can use tools like:
- `cron` (Linux/macOS)
- `schtasks` or Task Scheduler (Windows)
- **Container orchestration jobs**

These jobs help with both **initial execution** and **recurring access**.

---

### 9. **Serverless Execution**

In cloud environments, adversaries might leverage **serverless computing**—like AWS Lambda, Azure Functions, or Google Cloud Functions—to execute code. This can be part of a broader automation pipeline, making it harder to trace.

---

### 10. **Shared Modules**

Sometimes, malicious code is embedded in or executed through **shared modules**—libraries or executables that are loaded by legitimate applications. These provide access to shared functionality and often go unnoticed during routine scans.

---

### 11. **Software Deployment Tools**

Adversaries can hijack **software deployment tools** already present in enterprise environments. These tools are used to distribute and install software at scale, so they provide a perfect opportunity to execute malicious code across many systems at once.

---

### 12. **System Services**

Attackers might interact with or create **system services or daemons** to run programs. On macOS and Linux, tools like `launchctl` or `systemd` are commonly targeted, while Windows has its own service management interfaces.

---

### 13. **User Execution**

In some cases, attackers rely on users to **unknowingly execute the code**. This could happen when someone:
- Clicks a malicious link
- Opens an infected file
- Interacts with a rigged image or media

This technique is often paired with **social engineering**.

---

### 14. **WMI (Windows Management Instrumentation)**

WMI provides a **powerful scripting interface** for administrative tasks in Windows. Adversaries can abuse WMI to:
- Execute payloads
- Query system information
- Maintain stealth through legitimate system tools

---

These techniques represent **how the attacker actually runs their code**—a pivotal stage in the cyber kill chain. Next up, we’ll look at what attackers do **after the execution phase**, such as gaining persistence or escalating privileges.

Stay tuned for **Part 5** in the MITRE ATT&CK series!
