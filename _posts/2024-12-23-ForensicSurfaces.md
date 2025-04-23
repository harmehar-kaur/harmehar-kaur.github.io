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
2	DETECTING INCIDENTS ON LINUX DISK: KEY FORENSIC SURFACES
2.1	OVERVIEW
	Linux disk surfaces refer to filesystem areas where attackers might leave traces of their activities. Analyzing these surfaces is critical for forensic investigations and understanding the scope of a security incident. This guide explores common areas and methods to detect malicious activities on Linux filesystems.
________________________________________
2.2	KEY DISK SURFACES AND THEIR FORENSIC SIGNIFICANCE
2.2.1	CONFIGURATION FILES
	Attackers may modify sensitive configuration files to create backdoors or elevate privileges. These files are essential for forensic analysis:
o	/etc/passwd
	Stores user account details (excluding passwords).
	Key fields: username, user ID (UID), group ID (GID), home directory, and shell.
o	/etc/shadow
	Contains hashed passwords.
	Restricted access; often targeted in brute-force or privilege escalation attempts.
o	/etc/group
	Defines groups and their associated users.
	Review for unauthorized group memberships or the creation of new groups.
o	/etc/sudoers
	Configures sudo permissions.
	Look for modifications that grant attackers elevated privileges.
2.2.2	Investigating Installed Packages
	Attackers may install malicious packages to execute harmful scripts or maintain persistence. Forensic analysts should focus on:
o	Listing Installed Packages
	Command: dpkg -l
	Examine the list for suspicious or unknown packages.
o	Examining dpkg.log
	Log file: /var/log/dpkg.log
	Look for unusual installation activities and timestamps.
	Example command: grep " install " /var/log/dpkg.log
2.2.3	Malicious Scripts in Package Installations
	Some malicious packages include scripts executed automatically upon installation:
o	Package Metadata
	Stored in the DEBIAN/control file within the package directory.
	Review metadata for unusual descriptions or maintainers.
o	Post-Installation Scripts
	Malicious scripts often reside in DEBIAN/postinst.
	Check permissions and execution history of such scripts.
o	File Permissions
	Verify permissions to ensure only trusted users can modify or execute these scripts.
	Command: chmod to modify permissions.
2.2.4	Key Directories
	Attackers may place malicious files in critical directories:
o	System Services
	Path: /etc/systemd/system/
	Look for unauthorized services that execute malicious processes at startup.
o	Cron Jobs
	Path: /var/spool/cron/
	Review cron jobs for scheduled execution of malicious scripts.
o	Temporary Files
	Path: /tmp/
	Temporary files may host malicious executables or scripts.
