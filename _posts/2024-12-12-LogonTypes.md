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
Logon Event Types: 
• These store information about the nature of account authorisations on a system. These 
enable investigators to gather knowledge about date, time, username, hostname, and 
success/failure status of a logon, along with determining by exactly what means a logon 
was attempted.  
• Win7+: %SYSTEM ROOT%\System32\winevt\logs\Security.evtx  
• Event ID 4624  
Logon type  
2 
Explanation 
Logon via console 
3 
Network logon  
4 
Batch logon 
5 
Windows service logon  
7 
Credentials used to unlock screen; 
RDP session reconnect  
8 
Network logon sending 
credentials(cleartext) 
233 | H K a u r 
9 
10 
Different credentials used than 
logged on user 
Remote interactive logon  
11 
12 
Cache credentials used to logon  
Cached remote interactive (like 
type 10) 
13 
Cached unlock (like type 7)

Successful/Failed Logons: 
• The information about profile account creation, attempted logons, and account usage is 
also stored in windows system at the location as follows:   
o Win7+: % SYSTEM ROOT%\System32\winevt\logs\Security.evtx  
4624 
4625 
Successful logon  
Failed logon  
4634 | 4647 
4648 
Successful log off 
Logon using explicit 
credential (runas) 
4672 
Account logon with 
superuser rights (admin) 
4720 
An account was created  
▪ Service Events: 
• Investigators may analyse logs for suspicious Windows service creation, persistence, and 
services started or stopped around the time of a suspected compromise. Service events 
also record account information. A large amount of malware and worms in the wild 
utilize Services more specific ones that are started on boot illustrate persistence 
(desirable in malware). Services can crash due to attacks like process injection. These are 
stored in the following location:  
o Win7+: %SYSTEM ROOT%\System32\winevt\logs\System.evtx  
o Win10+: %SYSTEM ROOT%\System32\winevt\logs\Security.evtx  
• Most relevant events are present in the System Log:  
o 7034 – Service crashed unexpectedly  
o 7035 – Service sent a Start/Stop control  
o 7036 – Service started or stopped  
o 7040 – Start type changed (Boot | On Request | Disabled)  
o 7045 – A service was installed on the system (Win2008R2+)  
• Auditing can be enabled in the Security log on Win10+: 4697 – A service was installed on 
the system (from Security log)  
