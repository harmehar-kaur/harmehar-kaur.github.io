---
title: Cyber threats And cyber attacks
date: 2024-04-08
categories: [Cyber Security Fundamentals]
tags: [Spoofing,DDOS,Worm, APT, Side Channnel attack, Insider threat]
author: Harmehar Kaur
image:
  path: /assets/cyber-prefix.png
  alt: 
---
Types of Cyber threats: 
o	Spoofing: This is an attack with the goal of gaining access to a target system through the use of a falsified identity. Spoofing can be used against IP addresses, MAC addresses, usernames, system names, wireless network SSIDs, email addresses, and many other types of logical identification.
o	DDOS: A denial-of-service (DoS) attack is a network resource consumption attack that has the primary goal of preventing legitimate activity on a victimized system. Attacks involving numerous unsuspecting secondary victim systems are known as distributed denial-of-service (DDoS) attacks.
o	Worm: Worms pose a significant risk to network security. They contain the same destructive potential as other malicious code objects with an added twist—they propagate themselves without requiring any human intervention.
o	On-path attack: In an on-path attack, attackers place themselves between two devices, often between a web browser and a web server, to intercept or modify information that is intended for one or both of the endpoints. On-path attacks are also known as man-in-the-middle (MITM) attacks.
o	Advanced persistent threat (APT) refers to threats that demonstrate an unusually high level of technical and operational sophistication spanning months or even years. APT attacks are often conducted by highly organized groups of attackers.
o	Malware: A program that is inserted into a system, usually covertly, with the intent of compromising the confidentiality, integrity or availability of the victim’s data, applications or operating system or otherwise annoying or disrupting the victim.
o	Phishing Attack: An attack that attempts to misdirect legitimate users to malicious websites through the abuse of URLs or hyperlinks in emails could be considered phishing.
o	Virus: The computer virus is perhaps the earliest form of malicious code to plague security administrators. As with biological viruses, computer viruses have two main functions—propagation and destruction. A virus is a self-replicating piece of code that spreads without the consent of a user, but frequently with their assistance—for example, a user must click on a link or open a file.
o	Trojan: Named after the ancient story of the Trojan horse, the Trojan is a software program that appears benevolent but carries a malicious, behind-the-scenes payload that has the potential to wreak havoc on a system or network. For example, ransomware often uses a Trojan to infect a target machine and then uses encryption technology to encrypt documents, spreadsheets, and other files stored on the system with a key known only to the malware creator.
o	Side-channel Attack: A side-channel attack is a passive, non-invasive attack to observe the operation of a device. Methods include power monitoring, timing and fault analysis attacks.
o	Insider threats: Insider threats are threats that arise from individuals who are trusted by the organization. These could be disgruntled employees or employees involved in espionage. Insider threats are not always willing participants. A trusted user who falls victim to a scam could be an unwilling insider threat.
o	Ransomware: Malware used for the purpose of facilitating a ransom attack. Ransomware attacks often use cryptography to “lock” the files on an affected computer and require the payment of a ransom fee in return for the “unlock” code.
VII.	Cyber-attacks: 
o	Definition: Security attacks or cyber-attacks are actions aimed at exploiting vulnerabilities or lacking security features in systems.
o	They serve various malicious purposes, such as stealing sensitive information, causing harm to systems, or extorting victims for ransom.
o	Different types of attacks can exploit the same vulnerabilities.
o	The objective of these attacks is often to disrupt services, steal data, or leverage unauthorized access for personal or financial gain.
o	Insider Attacks
	Carried out by individuals who work for the company, also known as disgruntled employees. 
	These attacks are difficult to combat with technical measures alone, as the insider may already have valid credentials to access systems. 
	Common motivations include revenge, dissatisfaction, or financial gain.
o	External Attacks: 
	Perpetrated by external agents or threat actors who are not affiliated with the company. 
	Attackers typically gain access by using stolen credentials or exploiting system vulnerabilities. 
	Goals often include financial gain, data theft, or disrupting business operations.
o	Active Attacks 
	These are the attacks that aim to modify system resources or disrupt normal operations. These are designed to disrupt normal operations by modifying or fabricating data, interrupting services, or altering system resources. These attacks involve tampering with the data stream or making misleading changes to system data.
	Impact: They typically compromise one or more of the following:
•	Availability: Preventing legitimate access to services or data.
•	Integrity: Modifying data in an unauthorized way.
•	Authenticity: Impersonating users or systems to gain trust. 
	Examples: 
•	Masquerading: Impersonating another user or device to gain unauthorized access. 
•	Replay Attack: Capturing and retransmitting valid data to gain unauthorized access. 
•	Modification of Data: Altering information without authorization. Repudiation: 
•	Fabrication: Inserting false or misleading information into data streams.
•	Denying the occurrence of an action to avoid responsibility. Denial of Service (DoS): Overloading a system to make it unavailable to legitimate users.
	Common active attacks: 
•	Denial-of-service (DOS): 
o	This attack aims to make a service unavailable to users by overwhelming it with excessive requests.
o	Example: On August 9, 2021, Yandex, a Russian tech giant, faced a record-breaking DoS attack with nearly 22 million requests per second (RPS).
o	Common Types of DoS Attacks:
	Ping Flooding: Attackers flood the target with ICMP echo requests (ping) packets. This saturates the network and consumes all available bandwidth, preventing legitimate requests from reaching the server.
	Application-level floods: These focus on overwhelming specific applications, such as HTTP or DNS, with requests that require significant processing power, causing the application to become unresponsive.
	Peer-to-peer attacks: These exploit peer-to-peer (P2P) networks by misdirecting peers to target servers, flooding them with requests from various sources.
	Buffer overflow attack: A memory buffer overflow can force a machine to consume all available hard disc space, memory, or CPU time in a buffer overflow attack. This type of exploit frequently causes sluggishness, system failures, or other harmful server behaviors, resulting in a denial-of-service attack.
	Flooding attack: In this attack, a hostile actor can oversaturate server capacity by flooding a targeted server with an excessive volume of packets, resulting in denial-of-service. The attacking actor must have more accessible bandwidth than the target in order for most DOS flood assaults to succeed.
o	Mitigation Techniques:
	Contact ISP for support: ISPs can provide tools and services to mitigate DoS attacks by filtering unwanted traffic.
	Use SYN cookies: SYN cookies help defend against SYN flood attacks by avoiding the allocation of resources for connection requests until the handshake process is complete.
	Setup firewall and router: Proper configuration can block incoming traffic from known malicious sources.
	Employ reliable security software: Ensure that systems have up-to-date security solutions that can handle various types of DoS threats.
o	DOS Attack Prevention Steps:
	Analyse and monitor network traffic
	Create a DOS Response Plan
	Ensure that your network is secure.
	Keep an eye out for DOS Attack Warning Signs.
	Limit Network Broadcasting.
•	Modification of data: 
o	Tampering with assets to alter data, also considered an integrity attack.
o	Example: CVE-2022-0847 (Dirty Pipe) allows privilege escalation in Linux by overwriting arbitrary read-only files.
o	Fabrication (Active Attack): Generating false data to mislead users or systems.
o	Masquerade: When an attacker assumes another's identity to commit cybercrime.
o	Detection Techniques:
	File hash collection: Collecting hashes of critical files can help detect unauthorized changes, as modifications to files will result in a hash mismatch.
	File monitoring: Continuous monitoring of important files can alert administrators to suspicious changes.
o	Prevention Techniques:
	Signed binaries for code authentication.
	Limit program execution.
	Protect folders with file system access restrictions.
	Examples of Masquerade Techniques: APT32 disguised as flash installer, Ransomware like Ramsay disguised as JPGs, etc.
o	Passive Attacks: 
	Seek to gather information from the system without altering or damaging its resources. 
	Focus on monitoring or eavesdropping on data transmissions to obtain sensitive information. 
	Techniques: 
•	Eavesdropping: Listening in on communication between parties. 
•	Traffic Analysis: Analysing communication patterns to infer information. 
•	Foot printing: Collecting information about a system for future attacks. 
•	Dumpster Diving: Searching for discarded information in physical trash that could be useful. 
•	Wardriving: Searching for and exploiting wireless networks in a particular area. 
•	Spying: Observing sensitive data or operations within an organization. 
•	Tools: Wireshark, TCP-dump, and other network traffic monitoring tools.
	Common passive attacks: 
•	Eavesdropping: 
o	Listening to private communications or intercepting network traffic, often exploiting unencrypted interactions.
o	Impact: Financial loss, identity theft, and privacy invasion.
o	Methods:
o	Pickup Device: Physical devices that intercept electronic signals.
o	Transmission Link: Weaknesses in communication lines.
o	Listening Post: Setting up a station to capture wireless or wired communication.
o	Weak Passwords: Exploiting systems with easy-to-guess passwords.
o	Open Networks: Taking advantage of unsecured networks.
•	Foot-printing: 
o	Gathering as much information as possible about a system or organization to build a profile for attacks.
o	Identifying network architecture, application types, and the physical location of systems.
o	This is a preparatory phase for other attacks, often involving social engineering and publicly available information.
o	It is an ethical hacking approach that collects as much information as possible about a targeted computer system, infrastructure, and networks in order to find ways to break into them. 
o	Types: Active and passive 
o	Tools for foot-printing: 
	Google Dorks and Search Engines: Google dorking is a hacking tactic that involves utilizing Google Search and other Google tools to look for security flaws in website setup and computer code.
	NSLookup: Name server lookup (nslookup) is a network management command line tool for querying the Domain Name System (DNS) for the mapping between domain name and IP address, as well as other DNS data.
nslookup wikipedia.com
Server: 209.222.18.222
Address: 209.222.18.22253
Nonauthoritative answer:
Name: wikipedia.com
Address: 208.80.154.224
	Whois Lookup: A Whois domain lookup can be used to find out who owns a domain name and how long they've had it. All domain name registries keep a record of information about every domain name purchased through them, including who owns it and when it was obtained.
	Traceroute and tracert: These are computer network diagnostic procedures for presenting various routes (paths) and evaluating packet transit delays across an IP network. traceroute example.com
	WhatWeb: WhatWeb is a website reconnaissance tool that recognizes webpages' content management systems (CMS), blogging platforms, statistic/analytics packages, JavaScript libraries, web servers, and embedded devices.
	pOf: It is a tool for passively fingerprinting TCP/IP stacks. It can try to determine which systems are operating on machines that send network traffic to the box it's on, or on machines that share a medium with it.
	Reconng: Reconng is a free and opensource tool built on Open-Source Intelligence (OSINT). It is a simple and effective reconnaissance instrument.
	Nikto: Nikto is an opensource web server scanner that scans web servers for a variety of things, including over 6700 potentially harmful files/programs, outdated versions on over 1250 sites, and version specific issues on over 270 servers.
o	Benefits of Footprinting
	Footprinting assists firms in identifying and securing IT infrastructure before a threat actor exploits a flaw.
	It also aids businesses in better understanding their existing security posture by analyzing data about the firewall, security setup, and other factors.
	A network map aids in covering all trusted routers, servers, and other network topologies.
o	Countermeasures for Footprinting
	Configure routers to limit responses to footprinting queries.
	Use firewalls to restrict ports and avoid unauthorized port scans.
	Prevent web pages from being cached by search engines.
	Publish only what you wish to make public, nothing else.
	Use services that allow you to register anonymously.
•	Dumpster diving:
o	Searching through discarded items, such as paper documents or old devices, for sensitive information.
o	Goal: To find valuable information like usernames, passwords, network diagrams, or any useful data that can be exploited for unauthorized access
•	Wardriving 
o	Using a vehicle to locate unsecured or vulnerable Wi-Fi networks by using a laptop, smartphone, or portable antenna.
o	Purpose: Typically to steal an internet connection or gather information about networks for a future attack.
•	Spying: 
o	Intruders impersonate legitimate users to access and monitor network traffic, sometimes using a network adapter in promiscuous mode to capture all data on the network.
o	A successful cyberattack may seriously harm organizations or systems, as well as a company's reputation and consumer confidence. Economic Loss, Reputational Loss, and Legal Ramifications are all possible outcomes.
o	Mitigation strategies: 
o	Identify Sensitive Data: Classify and tag data based on its sensitivity to ensure it receives appropriate levels of protection.
o	Strong Passwords and Limited Access: Enforce complex passwords and limit access to critical resources only to authorized users.
o	Encryption: Encrypt data both in transit and at rest to protect it from unauthorized access or interception.
o	Network Protection: Use firewalls, Intrusion Detection Systems (IDS), and Intrusion Prevention Systems (IPS) to monitor and control network traffic.
o	Employee Training: Conduct regular training sessions to educate employees about security best practices and the latest attack vectors, such as phishing and social engineering.
o	Secure Software: Use software with built-in security features and apply updates regularly to address new vulnerabilities.
o	For Active Attacks: Use firewalls, IDPS, random session keys, OTPs, Kerberos authentication, and honeypots.
o	For Passive Attacks: Encrypt data using symmetric or asymmetric encryption and keep sensitive data private.
o	Prevention: 
o	Web Application Firewall (WAF)
	Purpose: Protects web applications by monitoring HTTP requests to detect and block malicious traffic.
	Functionality:
	Detects and stops inbound threats (e.g., code injection attempts).
	Blocks outbound threats, such as malware trying to communicate with a command-and-control (C&C) server.
o	 DDoS Protection 
	Purpose: Defends networks or servers against Distributed Denial of Service (DDoS) attacks.
	Mechanism: Uses specialized equipment on-premises or cloud-based services to monitor and distinguish between legitimate and malicious traffic.
	Outcome: Prevents server overload by mitigating attack traffic while allowing legitimate traffic through
o	Bot Protection
	Purpose: Prevents malicious bots from overloading websites or consuming resources.
	Functionality: Differentiates harmful bots from legitimate bots, such as those used for search indexing and performance monitoring.
	Impact: Reduces strain on systems by blocking harmful bots while allowing useful ones.
o	Cloud Security
	Purpose: Secures company assets in cloud environments, where infrastructure, applications, and data are stored and managed.
	Challenges:
	Vulnerable to cyber-attacks due to exposure to public networks.
	Low visibility and high dynamism make cloud systems difficult to monitor and secure.
	Solution: Implementing cloud-specific security policies and monitoring tools to enhance visibility and protect against threats. 
o	Database Security
	Purpose: Protects databases that hold sensitive and critical data.
	Techniques:
	Hardening database servers.
	Implementing access control and encryption.
	Continuous monitoring for malicious activities.
	Outcome: Prevents unauthorized access, data breaches, and manipulation of sensitive information.
o	API Security
	Purpose: Secures Application Programming Interfaces (APIs) used by applications to communicate with other systems.
	Challenges: Public APIs are particularly vulnerable to attacks due to exposure.
	Protection Techniques:
	Implementing multifactor authentication (MFA).
	Securing authentication tokens.
	Encrypting data in transit.
	Sanitizing user inputs to prevent injection attacks.
o	Threat Intelligence 
	Purpose: Gathers data on emerging and existing cyber threats from various sources.
	Functionality:
	Collects data from diverse threat feeds to identify indicators of compromise (IOCs).
	Helps understand threat actor motives and operational methods.
	Facilitates a faster, more informed response to security incidents.
	Benefit: Provides organizations with actionable insights to proactively defend against cyber threats.
o	Some other attacks: 
Injection Attacks
o	Definition: Injecting data to alter a program's behaviour.
o	Types of Injection Attacks:
•	SQL Injection: Manipulating SQL queries to extract or modify database information.
•	Cross-Site Scripting (XSS): Injecting malicious scripts into web pages to steal information from other users.
•	LDAP Injection: Targeting LDAP queries to manipulate directory information.
•	OS Command Injection: Inserting commands that the operating system executes.
o	Examples: XML Injection, Code Injection, XSS, SQL Injection, LDAP Injection, etc.
o	Mitigation: Employ secure coding practices like input validation, parameterized queries, and regular security assessments.
 
Advanced Persistent Threats (APTs)
o	Definition: Long-term cyber-attacks aimed at maintaining a presence in a network to steal sensitive data.
o	Examples of APT Groups: Fancy Bear, Cozy Bear, Helix Kitten, Wicked Panda, etc.
o	Definition: APTs are prolonged and carefully orchestrated attacks where attackers establish and maintain an undetected presence in a network to steal sensitive data over time.
o	Characteristics: APT attacks are meticulously planned and often target large organizations or government entities with high-value data.
o	Examples of APT Groups:
•	Fancy Bear (APT28): A Russian cyber-espionage group known for targeting government and military organizations.
•	Cozy Bear (APT29): Another Russian group associated with intelligence gathering.
•	Helix Kitten (APT34): Linked to cyber-attacks from the Middle East, targeting energy and telecommunications sectors.
•	Wicked Panda (APT41): A Chinese hacking group known for espionage and financially motivated attacks.
 
Social Engineering
o	Definition: Attacks leveraging human psychology to manipulate users into revealing sensitive information.
o	Types of Attacks: 
•	Phishing: Sending fraudulent emails or messages to trick users into revealing information.
•	Vishing (Voice Phishing): Using phone calls to impersonate legitimate entities and steal information.
•	Smishing (SMS Phishing): Sending fake SMS messages to trick recipients.
•	Baiting: Enticing victims with offers or rewards to lure them into malicious actions.
•	Tailgating: Physically following someone into a restricted area to gain unauthorized access.
•	Pretexting: Creating a fabricated scenario to manipulate someone into providing information.
•	Spear Phishing: Targeted phishing at specific individuals or organizations with personalized messages.
o	Stages of Social Engineering Attacks:
•	Preparation: The attacker gathers information on the target.
•	Infiltration: The attacker establishes a connection with the target, typically through communication (email, phone).
•	Exploitation: The attacker gains the trust of the target and manipulates them into divulging information.
•	Disengagement: The attacker exits the interaction once the goal is achieved.
o	Mitigation Techniques:
•	Avoid Unsolicited Communication: Be cautious with unexpected calls, messages, or emails.
•	Avoid Downloading from Unknown Sources: Only download from trusted sites to reduce malware risk.
•	Manually Type URLs: Instead of clicking on email links, type the URL directly into the browser.
•	Check for HTTPS and Padlock Icon: Verify site security in the browser address bar.
•	Never Share Personal Information: Don’t reveal sensitive information over email or phone.
•	Multi-factor Authentication (MFA): Adds an extra layer of security.
•	Regular Software Updates: Ensures protection from vulnerabilities.
•	Strong Passwords: Use complex passwords and update them periodically.
o	Social engineering is an important part of any security awareness training program for one simple reason: bad actors know that it works.
o	For cyber attackers, social engineering is an inexpensive investment with a potentially high payoff. Social engineering, applied over time, can extract significant insider knowledge about almost any organization or individual.
o	One of the most important messages to deliver in a security awareness program is the real and powerful threat of social engineering. Employees must become familiar with types of social engineering so that they can recognize and resist these attacks. 
o	Most social engineering techniques are not new. Many have even been taught as basic fieldcraft for espionage agencies and are part of the repertoire of investigative techniques used by real and fictional police detectives.
o	A short list of the tactics that we see across cyberspace currently includes:
•	Phone phishing or vishing: Using a rogue interactive voice response (IVR) system to recreate a legitimate-sounding copy of a bank or other institution’s IVR system. For example, the victim is prompted through a phishing email to call in to a “bank” via a provided phone number to verify information such as account numbers, account access codes, or a PIN and to confirm answers to security questions, contact information, and addresses. A typical vishing system will reject logins continually, ensuring the victim enters PINs or passwords multiple times, often disclosing several different passwords. More advanced systems may be used to transfer the victim to a human posing as a customer service agent for further questioning.
•	Quid pro quo: A request for your password or login credentials in exchange for some compensation, such as a “free gift,” a monetary payment, or access to an online game or service. If it sounds too good to be true, it probably is.
•	Pretexting: The human equivalent of phishing, where someone impersonates an authority figure or a trusted individual in an attempt to gain access to login information. The pretexter may claim to be an IT support worker who is supposed to do maintenance or an investigator performing a company audit. Or they might impersonate a co-worker, the police, a tax authority, or some other seemingly legitimate person. The goal is to gain access to a computer and information.
•	Tailgating: The practice of following an authorized user into a restricted area or system. The low-tech version of tailgating occurs when a stranger asks you to hold the door open behind you because they forgot their company RFID card. In a more sophisticated version, someone may ask to borrow your phone or laptop to perform a simple action when they are actually installing malicious software onto your device.
o	Social engineering works because it plays on human tendencies. Education, training, and awareness work best to counter or defend against social engineering because they underscore that every person in the organization plays a role in information security.
 
Bots 
o	Bots are automated, which means they follow instructions without requiring a human user to set them up manually every time. 
o	Forms of Bots: 
•	Chatbots 
•	Web crawlers 
•	Social bots 
•	Malicious bots 
o	Bots Can be classified into 
•	Spyware: Used to gather information of users without their knowledge. Example: Keyloggers 
•	Adware: Mainly used for promotions of products. Not so harmful. 
 
Malware
o	Malware, sometimes known as "malicious software, " is a catch-all word for any malicious program or code that is destructive to computers. 
o	Malware is hostile, invasive, and purposefully malicious software that aims to infiltrate, damage, or destroy computers, computer systems, networks, tablets, and mobile devices by gaining partial control over their activities. 
o	Malware Infection 
•	Your computer slows down 
•	Your screen is inundated with annoying ads. 
•	Your system crashes 
•	You notice a mysterious loss of disk space 
•	There's a weird increase in your system's Internet activity 
•	Your browser settings change 
•	Your antivirus product stops working 
•	You lose access to your files or your entire computer 
 
Ransomware 
o	'Ransomware' is a sort of malware that infects and takes control of a computer user's system, as well as the data and documents saved on it, in order to extort money from them. 
o	Typically, ransomware will either 'lock' the computer to restrict regular use or encrypt the machine's documents and files to prevent access to the saved data. 
 
Drive-By Download: 
o	Malicious apps that install on your devices without your knowledge or agreement. 
o	Unintentional downloads of any files or associated software onto a computer device are also included. 
o	This might happen when the user is viewing a genuine website or as a result of malicious advertising shown on a seemingly safe website. 
o	Drive-by downloads Working 
•	Injection 
•	Vulnerability exploits 
•	Download 
•	Execution 
•	Remote control 
•	Lateral movement 
o	Drive by Download Mitigation 
•	Application whitelisting 
•	Next-generation antivirus (NGAV) 
•	Threat intelligence 
•	User and entity behaviour analytics (UEBA) 
•	Endpoint detection and response (EDR) 
 
Website defacement
•	Web defacement is an attack in which malevolent actors like Script.
•	Website Defacement Prevention Steps:
o	Use the Principle of Least Privilege (POLP).
o	Use add-ons and plugins cautiously.
o	Limit displaying of Error Messages.
o	Use Secure Socket Layer (SSL)/ Transport Layer Security (TLS).
o	File uploads should be limited.
Brute force Attacks
o	Simple Brute Force Attacks
•	Definition: Involves trying every possible combination of characters until the correct password is found.
•	Approach: This method doesn’t rely on dictionaries or patterns; it systematically tests all possible passwords.
•	Drawbacks: Extremely time consuming, especially for long or complex passwords.
o	Dictionary Attacks
•	Definition: Uses a predefined list of likely passwords (dictionary) instead of testing all possible combinations.
•	Approach: The attacker tries passwords from a dictionary that contains commonly used or previously leaked passwords.
•	Effectiveness: Faster than simple brute force but limited to words in the dictionary.
o	Hybrid Brute Force Attacks
•	Definition: Combines dictionary attacks with brute force techniques.
•	Approach: Starts with a dictionary of common passwords and then adds variations, such as numbers or symbols, to extend the guessing attempts.
•	Use Case: Effective when users create passwords based on common words with slight modifications.
o	Reverse Brute Force Attacks
•	Definition: Begins with a known password (often one from a data breach) and applies it to multiple usernames.
•	Approach: Targets a large number of accounts with the same password rather than targeting a specific account.
•	Risk: Especially dangerous when users reuse passwords across multiple accounts.
o	Credential Stuffing
•	Definition: Involves using known username-password pairs from previous data breaches to gain unauthorized access.
•	Approach: Attackers try these leaked credentials on different websites, hoping for success due to reused passwords.
•	Prevention: Multifactor authentication and avoiding password reuse can mitigate this risk.
o	Preventive Measures:
•	Use Strong Passwords: Encourage complex, unique passwords for each account.
•	Account Lockouts: Limit login attempts to prevent repeated brute force attempts.
•	Multi-Factor Authentication (MFA): Adds an extra layer of security beyond passwords.
•	Password Hashing and Salting: Securely store passwords so that even if they’re stolen, brute force attempts are less likely to succeed.

