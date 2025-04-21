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
System Boot and Startup and shutdown:  
▪ System Boot and auto-start programs: 
• System Boot programs are lists of programs that will run on system boot 
• Registry keys also store information about programs that are run when a user logs on 
(auto-start programs). 
• Location  
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run 
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce 
o SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce 
o SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run 
o SOFTWARE\Microsoft\Windows\CurrentVersion\Run  
o SYSTEM\CurrentControlSet\Services  
• If Start value is set to 0x02, then service application will start at boot (0x00 for drivers) 
Interpretation 
• Useful to find malware and to audit installed software  
• This is not an exhaustive list of autorun locations 
▪ System Last Shutdown time:  
• The last time the system was shut down is also stored in windows and in windows XP the 
number of times the shutdown is done is also recorded. This time could help 
investigators the last activity time on system of interest and help detect user behaviour 
and system anomalies along with Windows 64-bit FILETIME format. These are stored at 
the following:  
o SYSTEM\CurrentControlSet\Control\Windows (Shutdown Time) 
o SYSTEM\CurrentControlSet\Control\Watchdog\Display (Shutdown Count – 
WinXP only)  
