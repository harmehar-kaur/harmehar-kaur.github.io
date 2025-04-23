---
title: Linux Forensic Artefacts You Should Know About  
date: 2024-12-24  
categories: [DFIR]  
tags: [Linux Forensics, System Artefacts, Incident Response, Forensic Analysis, DFIR]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Linux System Artefacts Forensics  
---

When it comes to investigating a compromised Linux system, artefacts are everything. These bits of leftover evidence tell the story—what was done, by whom, and how. Whether you're a digital forensic analyst or just curious about what's under the hood, here's a practical walkthrough of the key artefacts that help piece things together during a Linux investigation.

---

### System Information

Understanding the system's baseline configuration is the first step.

- `uname -a` – Displays kernel and version info.
- `/proc/version`, `/proc/cpuinfo` – Detailed system specs.
- `dmesg` – Kernel ring buffer messages.

**Why it matters:** Knowing the kernel version and hardware specs can reveal known vulnerabilities or whether a targeted exploit might have been used.

---

### /var/log Directory

Logs are the black boxes of Linux systems—they record everything if configured right.

- `auth.log` or `secure` – Authentication logs.
- `syslog` – System-wide events.
- `apache2/access.log`, `apache2/error.log` – Web server activity.
- `dpkg.log` – Software package activity.

**Why it matters:** These logs can show user actions, system changes, login attempts, or suspicious events at specific times.

---

### Shell History

A simple yet often revealing artefact.

- `~/.bash_history` – Bash shell history.
- `~/.zsh_history`, `~/.ash_history` – Other shell types.

**Why it matters:** You can trace the attacker’s command-line activities. Just be aware that history files can be wiped or altered.

---

### Filesystem

The filesystem is where most of the action happens, and it leaves trails.

- `/etc/` – Critical configuration files.
- `/home/` – User data and personal directories.
- `/tmp/` – Temporary files; often abused for storing or running malware.

**Why it matters:** File metadata shows ownership, access times, and can lead you to suspicious files or recent changes.

---

### User Accounts

Attackers love adding users or escalating privileges quietly.

- `/etc/passwd` – User accounts.
- `/etc/shadow` – Hashed passwords.
- `/etc/group` – Group memberships.

**Why it matters:** Spotting new users or changes to existing ones could be the first clue to a breach.

---

### Application Data

Applications leave behind useful evidence of how they were used—or misused.

- Application data in `/var/` or `/etc/`.
- User-specific settings in `~/.config/`.

**Why it matters:** These can reveal usage patterns, cached credentials, or logs of attacker activities.

---

### Networking

If there’s one thing attackers rely on, it’s networking. And it leaves a trail.

- `/var/log/syslog` – General network logs.
- `/var/log/messages` – System-level logging including network services.
- Firewall logs – `iptables`, `ufw`, etc.
- `/proc/net/`, or tools like `netstat` and `ss` – Show active connections.

**Why it matters:** You can spot connections to shady IPs, unexpected open ports, or unusual traffic patterns.

---

### Services

Services are prime candidates for persistence mechanisms.

- `/etc/systemd/system/` – Modern service configurations.
- `/etc/init.d/` – Legacy service scripts.
- Cron jobs:  
  - `/var/spool/cron/`  
  - `~/.cron*`

**Why it matters:** Malicious services or scheduled jobs could indicate backdoors or scheduled payloads.

---

### External Devices

Removable media often play a role in data exfiltration or malware delivery.

- `/media/` – Mounted external devices.
- `/dev/` – Device files.
- Logs:  
  - `/var/log/syslog`  
  - `/var/log/messages`

**Why it matters:** Detects USB usage or external drives used to extract or deliver files.

---

### Remote Connections

Remote access is common in attacks—and it’s traceable.

- `/var/log/auth.log` or `/var/log/secure` – SSH logs.
- VPN logs (depends on software used).
- Command: `last` – Shows recent logins and IPs.

**Why it matters:** Helps pinpoint unauthorized remote sessions and potential attacker IPs.

---

That wraps up the major artefacts you should be tracking in a Linux forensic investigation. Each of these tells a part of the bigger story—and when you line them up, the incident becomes much clearer.
