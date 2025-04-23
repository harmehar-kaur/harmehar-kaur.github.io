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
after windows forensics let's get a brief about the linux forensics as well. 

1	INCIDENT SURFACE 
•	All potential points or sources in the Linux system where an incident could occur or traces of incidents could be found. This could lead to a security breach, which could also be part of the Linux Attack Surface, which refers to various entry points where an attack or unauthorized attempt could be made to enter the system or gain unauthorized attempts.
1.1	LINUX ATTACK SURFACE VERSUS LINUX INCIDENT SURFACE 
1.1.1	Linux Attack Surface
•	The Linux Attack Surface refers to all possible points of interaction within a Linux system that an adversary might exploit to gain unauthorized access or perform malicious activities. The primary objective is to reduce the attack surface to limit potential entry points for attackers.
•	Key Entry Points in the Attack Surface:
o	Open Ports: Unsecured or misconfigured ports accessible externally.
o	Running Services: Services that may have vulnerabilities or misconfigurations.
o	Software Vulnerabilities: Outdated or insecure applications.
o	Network Communication: Insecure protocols or exposed interfaces.
•	Strategies to Minimize the Attack Surface:
o	Patch Vulnerabilities: Regularly update and patch systems and software.
o	Disable Unnecessary Services: Minimize the use of services that are not required.
o	Secure User Interfaces: Check and harden interfaces where users interact with the system.
o	Restrict Public Exposure: Limit public-facing services, applications, and ports.
1.1.2	Linux Incident Surface
•	The Linux Incident Surface encompasses all areas of a system where security breaches can be detected, analysed, and mitigated post-compromise. It is focused on detecting, managing, and responding to actual security incidents.
•	Purpose of Identifying the Incident Surface:
o	To hunt, detect, and respond to security incidents effectively.
o	To recover from the incident and mitigate further damage.
•	Key Points in the Incident Surface:
o	System Logs: 
	Examples: auth.log, syslog, krnl.log.
	Contain records of system activities, authentication attempts, and kernel events.
o	Network Traffic: Monitoring suspicious connections and data flows.
o	Running Processes: Identifying unusual or unauthorized processes.
o	Running Services: Checking services for unauthorized modifications or suspicious activity.
o	File and Process Integrity: Detecting unauthorized changes to critical files and binaries.
1.1.3	Comparison of Attack Surface and Incident Surface
Aspect	Linux Attack Surface	Linux Incident Surface
Purpose	Reduce potential entry points for attackers.	Detect, analyse, and respond to incidents.
Focus	Prevention and hardening against attacks.	Post-compromise detection and recovery.
Key Areas	Open ports, running services, software vulnerabilities, network communication.	Logs, processes, services, network traffic, file integrity.
Goal	Minimize vulnerabilities and exposures.	Identify attack traces and mitigate impacts.

1.2	PROCESSES AND NETWORK COMMUNICATION IN LINUX INCIDENT SURFACE
•	Processes and network communication are critical areas of investigation in the Linux Incident Surface. Monitoring and analysing processes, particularly those that interact with external systems or network resources, can reveal evidence of unauthorized or malicious activity. This subpart of the incident surface focuses on identifying suspicious processes and their associated network communications to detect and respond to security incidents effectively.
•	Processes running on a Linux system may provide insight into potential malicious activity. To effectively analyze processes, the following steps are typically undertaken:
o	Identifying Running Processes: Use tools to list all running processes on the system. A detailed view can reveal processes initiated by unexpected users, processes consuming unusual amounts of resources, or those running from suspicious directories like /tmp.
o	Filtering Suspicious Processes: Processes that meet certain criteria may warrant further investigation:
	Running from temporary or user directories.
	Initiated by unauthorized users or appearing as orphan processes.
	Processes linked to a suspicious parent-child relationship.
	Processes with unusual command-line arguments or binary locations.
o	Inspecting Process Details: Gather detailed information about processes, including:
	Owner (user or system).
	Process ID (PID).
	Memory and CPU usage.
	Start time and associated terminal.
	Libraries, files, or resources utilized.
•	Network communication associated with processes can highlight potential threats, especially those establishing external connections. The following actions are integral to examining network communication:
o	Identifying Active Connections: Tools can display network activity, showing open ports, active connections, and processes interacting with external servers or IP addresses.
o	Tracing Process-Connection Mapping: By correlating process details (via their PID) with active network connections, analysts can determine:
	Local and remote IP addresses.
	Ports involved in communication.
	Protocols used (TCP/UDP).
o	Detecting Suspicious Behavior: Look for processes that:
	Communicate with known malicious IPs or domains.
	Use non-standard ports for data transmission.
	Open unusually high numbers of connections.
•	Various tools are used to investigate processes and network communications effectively:
o	ps Command: Displays running processes and provides detailed information on their state, resource usage, and origin.
o	lsof: Lists open files and network connections associated with specific processes or PIDs.
o	osquery: Allows querying processes, sockets, and network connections in a structured format for deeper analysis.


