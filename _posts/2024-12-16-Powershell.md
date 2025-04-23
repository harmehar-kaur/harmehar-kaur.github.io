---
title: Searching for Artifacts on Windows via PowerShell
date: 16 December 2024
categories: [DFIR]
tags: [PowerShell, Windows, Digital Forensics, Cybersecurity]
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: PowerShell Forensics
---

# Searching for Artifacts on Windows via PowerShell

Today, we're diving into a practical guide to identifying suspicious activity on Windows systems using PowerShell. Whether you're working in digital forensics or just interested in how attackers might leave traces on a machine, this blog will show you how you can use PowerShell scripts to find evidence of compromise.

## What Are We Looking For?

In the world of digital forensics, registry keys are essential for tracking system activity. The Windows registry is a huge database that holds configuration data for the operating system and other installed software. Attackers, when they gain access to a machine, often modify registry keys to conceal their tools, retrieve system info, or even configure auto-start programs. These malicious changes are the "artifacts" we're looking for. 

These artifacts are key indicators of compromise (IoC) and can give us insight into the attacker's activity. The good news is that PowerShell can be used to find these artifacts!

## How Does the PowerShell Script Work?

The script we're using works by scanning the registry for specific keys that are commonly associated with malicious activity. This is done using a dictionary of known registry artifacts, which can be tailored to your environment. 

Once the script runs, it checks two main areas in the Windows registry:

- **HKEYCURRENTUSER**: This registry key contains settings for the currently logged-in user.
- **HKEYLOCALMACHINE**: This key holds system-wide settings that apply regardless of who is logged in.

The script analyzes both of these areas to search for suspicious registry keys that may indicate the presence of malware, exploits, or ransomware. Afterward, it generates a detailed report, which can be reviewed to find out whether any harmful keys were detected.

### Key Registry Locations:

- **HKEYCURRENTUSER**: Stores personal settings for the logged-in user.
- **HKEYLOCALMACHINE**: Contains system-wide settings for all users.

## Example of Using the PowerShell Script

On our GitHub, you can find the script that automates the process of searching through these registry keys. Here's how it works:

- The user prepares a list of registry keys to search for.
- The script runs through the specified keys in the dictionary.
- If any of these keys are found in the registry, the tool flags them as potential evidence of compromise.

**Note**: You can modify the list of registry keys to match specific threats like malware, ransomware, or exploits.

---

## PowerShell Remoting Artifacts

PowerShell is not only useful for running commands locally, but it’s also commonly used for remote management. As PowerShell is a go-to tool for attackers, especially for lateral movement and fileless attacks, it’s important to track any remote PowerShell activity. One of the best ways to do this is by looking for artifacts related to PowerShell remoting, especially in event logs.

### Key Event IDs for PowerShell Remoting:

- **EventID 400 & 403**: These mark the beginning and end of a remote PowerShell session.
  - **EventID 400**: "Engine state is changed from None to Available."
  - **EventID 403**: "Engine state is changed from Available to Stopped."
  
- **EventID 169**: Marks the start of a remoting session, showing which authentication mechanism was used.
  
- **EventID 81, 82, 134**: These capture the low-level actions during a PowerShell session. Useful for tracking when a remote session was created and when it was deleted.

---

## Event Logs: Where PowerShell Logs Are Stored

If you're investigating a system and want to find PowerShell logs, you can find them in specific event log locations:

- **Windows PowerShell log**:
  - Path: `Applications and Services Logs > Windows PowerShell`
  - Description: Captures session start and stop events, along with basic execution details.

- **Microsoft-Windows-PowerShell/Operational log**:
  - Path: `Applications and Services logs > Microsoft > Windows > PowerShell > Operational`
  - Description: Contains detailed execution logs of scripts, including metadata about commands and events such as script block logging (Event ID 4104).

- **PowerShell Transcripts**:
  - Path: Typically stored in a user-defined or administrator-configured directory, such as `C:\Users\<UserName>\Documents\PowerShell_Transcripts`.

---

## The Importance of PowerShell Logs in Digital Forensics

PowerShell's versatility makes it a popular tool for legitimate system administrators but also a go-to for attackers. It can be used for fileless malware, lateral movement, and data exfiltration, making PowerShell logs invaluable in any forensic investigation.

Here’s a breakdown of some crucial PowerShell logs for forensic work:

### 1. Script Block Logging
Script block logging captures all executed PowerShell code, including obfuscated scripts. This is vital for catching malicious actors who try to hide their activities.

### 2. Module Logging
Module logging records the loading and execution of PowerShell modules, which are often used by attackers in their workflow.

### 3. PowerShell Operational Logs
These logs contain metadata about scripts and commands executed, including which user executed them. These are key to tracing an attack timeline.

### 4. PowerShell Transcripts
If enabled, these logs record all commands and their output within a PowerShell session, offering a comprehensive view of PowerShell usage.

---

## Pitfalls with PowerShell Logs

Despite their usefulness, there are some challenges with PowerShell logs:

- **Not enabled by default**: Many critical logs (e.g., Script Block Logging, Transcription Logging) are not enabled by default and need to be manually configured.
  
- **Log overwriting**: In high-traffic environments, logs may be overwritten before they can be analyzed, leading to data loss.

- **Obfuscation**: Attackers may obfuscate their PowerShell scripts to avoid detection, but with the right tools, you can de-obfuscate them.

- **Log manipulation**: Attackers may try to clear or disable logs to cover their tracks.

---

## Real-World Use Case: Network Intrusion Involving PowerShell

Let’s walk through an example where PowerShell logs helped identify an attack:

### 1. Initial Discovery:
A network intrusion was detected when unusual outbound traffic was spotted. After analyzing the PowerShell operational logs, the forensic team found obfuscated PowerShell commands (Event ID 4104) showing attempts to connect to a remote server.

### 2. De-obfuscation:
Using tools like CyberChef, the team was able to de-obfuscate the scripts, revealing that the attacker was attempting to establish a reverse shell connection.

### 3. Transcription Logs:
The transcription logs provided a full record of the PowerShell session, showing the attacker enumerating network shares and copying sensitive data.

### 4. Attack Timeline:
By combining script block logs and transcription logs, investigators pieced together the attack timeline, identified the initial phishing email, and traced the attacker's movements within the network.

### 5. Remediation:
Once the attack was fully understood, the team blocked the attacker’s C2 server and took steps to prevent similar attacks in the future.

---

## Conclusion

PowerShell logs are a goldmine for forensic investigators, particularly when dealing with advanced attacks like fileless malware and remote exploitation. While there are challenges, such as the need for proactive configuration and the potential for log manipulation, these logs provide crucial insights into attacker behavior. By properly enabling and analyzing these logs, investigators can uncover the full scope of a compromise and better understand the attacker's tactics, techniques, and procedures (TTPs).

For more tips on PowerShell forensics and other cybersecurity topics, stay tuned to our blog!

---

