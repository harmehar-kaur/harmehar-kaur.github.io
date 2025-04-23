---
title: Collecting Triage Data from Linux Systems Using UAC  
date: 2024-12-25  
categories: [DFIR]  
tags: [Linux Forensics, UAC, Triage Collection, Incident Response, Forensic Tools]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Collecting Linux Triage Data with UAC  
---

When responding to a security incident on a Linux system, having the right tools to quickly collect relevant data is crucial. One such tool that stands out for its simplicity and power is **UAC (Unix-like Artifact Collector)**. In this post, we’ll take a look at how UAC works, what it collects, and how to use it to gather triage data in a forensically sound way.

---

### What is UAC?

UAC is a lightweight, shell-based tool designed to collect forensic artefacts from Unix-like systems—including Linux. It's free, portable, and doesn't require installation, which makes it ideal for fast triage during incident response.

**Key Highlights:**
- Collects important forensic data like system logs, temporary files, browser histories, and running processes.
- Works from a single shell script.
- Requires minimal setup.
- Supports output storage via SFTP or S3, or can save to an external drive.

---

### What Can UAC Do?

Here’s a quick breakdown of what UAC brings to the table:

- Collects artefacts such as:
  - Browser history
  - `/var/log` contents
  - Files in `/tmp/`
  - Live system metadata and running processes
- Follows the **order of volatility**, ensuring more volatile data is collected first.
- Can detect and hash processes running **without an on-disk binary**.
- Supports **bodyfile** creation with detailed file attributes (especially for ext4).
- Gathers configuration files, user-specific data, and logs.
- Supports **volatile memory acquisition** via external tools.

---

### What’s in the UAC Package?

When you download and extract UAC, you'll find the following structure:

- **Artifacts** – Defines what items to collect (customizable).
- **Bin** – A place to include any extra binaries you'd like to use.
- **Tools** – Contains helper scripts for normalization and processing.
- **Profiles** – Defines which artefacts to collect. Comes with default profiles but you can add your own.
- **uac** – The main shell script that kicks off the collection.

---

### 4.1.3.1 How to Use UAC: Step-by-Step

Ready to get hands-on? Here’s how you can start using UAC:

1. **Download the latest release** from the official GitHub:  
   [https://github.com/tclahr/uac/releases](https://github.com/tclahr/uac/releases)

2. **Decompress the downloaded archive** using:
   ```bash
   tar -xf uac_file_downloaded_name.tar.gz
