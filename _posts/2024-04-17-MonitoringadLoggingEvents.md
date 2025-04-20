---
title: Monitoring and logging events 
date: 2024-04-17
categories: [Cyber Security Fundamentals]
tags: 
author: Harmehar kaur 
image:
  path: /assets/cyber-prefix.png
  alt: 
---
I.	Monitoring and logging events: 
o	The use of physical access controls, monitoring personnel and equipment entering and leaving, and auditing and logging all physical events are primary elements in maintaining overall organizational security.
o	Logging and monitoring the health of the information environment is essential to identifying inefficient or improperly performing systems, detecting compromises, and providing a record of how systems are used.
o	Monitoring: 
o	Cameras: Cameras are normally integrated into the overall security program and centrally monitored. Cameras provide a flexible method of surveillance and monitoring. They can be a deterrent to criminal activity, can detect activities if combined with other sensors and, if recorded, can provide evidence after the activity. They are often used in locations where access is difficult or there is a need for a forensic record. While cameras provide one tool for monitoring the external perimeter of facilities, other technologies augment their detection capabilities. A variety of motion sensor technologies can be effective in exterior locations. These include infrared, microwave, and lasers trained on tuned receivers. Other sensors can be integrated into doors, gates, and turnstiles, and strain-sensitive cables and other vibration sensors can detect if someone attempts to scale a fence. Proper integration of exterior or perimeter sensors will alert an organization to any intruders attempting to gain access across open space or attempting to breach the fence line.
o	Logs: physical logs, such as a sign-in sheet maintained by a security guard, or even a log created by an electronic system that manages physical access. A log is a record of events that have occurred. Physical security logs are essential to support business requirements. They should capture and retain information as long as necessary for legal or business reasons. Because logs may be needed to prove compliance with regulations and assist in a forensic investigation, the logs must be protected from manipulation. Logs may also contain sensitive data about customers or users and should be protected from unauthorized disclosure. The organization should have a policy to review logs regularly as part of their organization’s security program. As part of the organization’s log processes, guidelines for log retention must be established and followed. If the organizational policy states to retain standard log files for only six months, that is all the organization should have. A log anomaly is anything out of the ordinary. Identifying log anomalies is often the first step in identifying security-related issues, both during an audit and during routine monitoring. Some anomalies will be glaringly obvious: for example, gaps in date/time stamps or account lockouts. Others will be harder to detect, such as someone trying to write data to a protected directory. Although it may seem that logging everything to avoid missing any important data is the best approach, most organizations would soon drown under the amount of data collected. Business and legal requirements for log retention will vary among economies, countries, and industries. Some businesses will have no requirements for data retention. Others are mandated by the nature of their business or by business partners to comply with certain retention data. For example, the Payment Card Industry Data Security Standard (PCI DSS) requires that businesses retain one year of log data in support of PCI. Some federal regulations include requirements for data retention as well. If a business has no business or legal requirements to retain log data, how long should the organization keep it? The first people to ask should be the legal department. Most legal departments have very specific guidelines for data retention, and those guidelines may drive the log retention policy.
o	 Alarm System: Alarm systems are commonly found on doors and windows in homes and office buildings. In their simplest form, they are designed to alert the appropriate personnel when a door or window is opened unexpectedly. For example, an employee may enter a code and/or swipe a badge to open a door, and that action would not trigger an alarm. Alternatively, if that same door was opened by brute force without someone entering the correct code or using an authorized badge, an alarm would be activated. Another alarm system is a fire alarm, which may be activated by heat or smoke at a sensor and will likely sound an audible warning to protect human lives in the vicinity. It will likely also contact local response personnel such as the closest fire department. Finally, another common type of alarm system is a panic button. Once activated, a panic button will alert the appropriate police or security personnel.
o	 Security Guards: Security guards are an effective physical security control. No matter what form of physical access control is used, a security guard or other monitoring system will discourage a person from masquerading as someone else or following closely on the heels of another to gain access. This helps prevent theft and abuse of equipment or information.
o	Types of monitoring:
Ingress monitoring refers to surveillance and assessment of all inbound communications traffic and access attempts. Devices and tools that offer logging and alerting opportunities for ingress monitoring include:
•	- Firewalls
•	- IDS/IPS tools
•	- SIEM solutions
•	- Anti-malware solutions	Egress monitoring
Egress monitoring is used to regulate data leaving the organization’s IT environment. The term currently used in conjunction with this effort is data loss prevention (DLP) or data leak protection. The DLP solution should be deployed so that it can inspect all forms of data leaving the organization, including:
•	Email (content and attachments)
•	 Copy to portable media
•	File Transfer Protocol (FTP)
•	 Posting to web pages/websites
•	 Applications/application programming interfaces (APIs)


o	Logging:
o	Logging is the primary form of instrumentation that attempts to capture signals generated by events.
o	Events are any actions that take place within the systems environment and cause measurable or observable change in one or more elements or resources within the system.
o	Logging imposes a computational cost but is invaluable when determining accountability. Proper design of logging environments and regular log reviews remain best practices regardless of the type of computer system. Major controls frameworks emphasize the importance of organizational logging practices. Information that may be relevant to being recorded and reviewed include, but is not limited to:
•	User IDs
•	System activities
•	Dates/times of key events (e.g., logon and logoff)
•	Device and location identity
•	Successful and rejected system and resource access attempts
•	System configuration changes and system protection activation and deactivation events
o	Robust logging practices provide tools to effectively correlate information from diverse systems to fully understand the relationship between one activity and another.
o	Log reviews are an essential function not only for security assessment and testing but also for identifying security incidents, policy violations, fraudulent activities, and operational problems near the time of occurrence. Log reviews support audits, forensic analysis related to internal and external investigations, and provide support for organizational security baselines. Review of historic audit logs can determine whether a vulnerability identified in a system has been previously exploited.
o	It is helpful for an organization to create components of a log management infrastructure and determine how these components interact. This aids in preserving the integrity of log data from accidental or intentional modification or deletion and in maintaining the confidentiality of log data.
o	Controls are implemented to protect against unauthorized changes to log information. Operational problems with the logging facility are often related to alterations to the messages that are recorded, log files being edited or deleted, and storage capacity of log file media being exceeded. Organizations must maintain adherence to retention policy for logs as prescribed by law, regulations, and corporate governance. Since attackers want to hide the evidence of their attack, the organization’s policies and procedures should also address the preservation of original logs. Additionally, the logs contain valuable and sensitive information about the organization. Appropriate measures must be taken to protect the log data from malicious use.

