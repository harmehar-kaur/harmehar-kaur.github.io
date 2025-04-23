---
title: 
date: 
categories: 
tags: 
author: 
image:
  path: 
  alt: 
---
3	ARTEFACTS IN LINUX SYSTEM
	Forensic investigations on Linux systems involve identifying, extracting, and analyzing various artifacts that provide insights into system activity, user behaviours, and potential malicious actions. Below is an overview of key artifact locations and their relevance in Linux forensics.
3.1	SYSTEM INFORMATION
•	Location/Commands: 
o	uname -a (system kernel and version info)
o	/proc/ directory (e.g., /proc/version, /proc/cpuinfo)
o	dmesg (kernel message buffer)
•	Purpose: 
o	Provides details about the system environment, kernel version, and hardware, which can help identify vulnerabilities or specific configurations targeted by attackers.
3.2	/VAR/LOG DIRECTORY
•	Common Logs: 
o	auth.log or secure (authentication attempts)
o	syslog (general system events)
o	apache2/access.log and apache2/error.log (web server activity)
o	dpkg.log (package installations and removals)
•	Purpose: 
o	Logs can reveal user activity, system events, login attempts, package installations, and potential anomalies.
3.3	SHELL HISTORY
•	Location: 
o	~/.bash_history (Bash shell history)
o	Similar files for other shells: ~/.zsh_history, ~/.ash_history
•	Purpose: 
o	Provides a record of commands executed by the user.
o	Helps trace malicious commands or system interactions.
o	Beware: History can be cleared or tampered with by attackers.
3.4	FILESYSTEM
•	Key Areas: 
o	/etc/ (configuration files)
o	/home/ (user directories)
o	/tmp/ (temporary files, often used by malware)
•	Purpose: 
o	Tracks file creation, modification, and access times.
o	Metadata reveals file ownership and permissions.
o	Identifies recently modified or suspicious files.
3.5	USER ACCOUNTS
•	Key Files: 
o	/etc/passwd (user account information)
o	/etc/shadow (hashed passwords)
o	/etc/group (group memberships)
•	Purpose: 
o	Identifies unauthorized users or privilege escalation attempts.
o	Tracks changes in user accounts and group memberships.
3.6	APPLICATION DATA
•	Common Locations: 
o	Application-specific directories in /var/ or /etc/
o	User-specific application data in ~/.config/
•	Purpose: 
o	Analyzes application logs, preferences, and cached data for evidence.
o	Reconstructs user activities and application usage patterns.
3.7	NETWORKING
•	Key Artifacts: 
o	/var/log/syslog (network-related logs)
o	/var/log/messages (network service logs)
o	Firewall logs (e.g., iptables or ufw)
o	Open connections: netstat, ss, or /proc/net/
•	Purpose: 
o	Tracks network activity, including incoming/outgoing connections.
o	Identifies unusual traffic, such as connections to suspicious IPs or ports.
3.8	SERVICES
•	Key Locations: 
o	/etc/systemd/system/ (systemd service configurations)
o	/etc/init.d/ (legacy init services)
o	Cron jobs: /var/spool/cron/, ~/.cron*
•	Purpose: 
o	Examines running services for unauthorized or malicious processes.
o	Tracks scheduled tasks that could execute malware or maintain persistence.
3.9	EXTERNAL DEVICES
•	Key Locations: 
o	/media/ (mounted external devices)
o	/dev/ (device files)
o	Logs: /var/log/syslog, /var/log/messages for connection events.
•	Purpose: 
o	Tracks data transfers to/from USB drives or other external devices.
o	Identifies unauthorized use of external storage for data exfiltration.
3.10	REMOTE CONNECTIONS
•	Key Artifacts: 
o	SSH logs: /var/log/auth.log or /var/log/secure
o	VPN configurations/logs (application-specific locations)
o	Command: last (shows recent logins, including remote sessions)
•	Purpose: 
o	Analyses remote access to the system.
o	Identifies unauthorized connections or potential attackers’ IPs.
