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
Recent files/ documents:  
• Windows also store information about recently opened files and programs for all the 
users. Which is stored in the NTUSER hive. It also stores keys for different file extensions 
and gives us a list of last opened file for each extension say .pdf or .jpg etc.  Location of 
this information is:  
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDo
 cs\.pdf or any other extension whose information is required.  
• Like windows Microsoft office also maintains a list of recently opened files which is again 
stored in the NTUSER hive ate the location:  
o NTUSER.DAT\Software\Microsoft\Office\<Version>.  
• Starting from Microsoft 365 the location is tied to a live ID of the user which is:  
o NTUSER.DAT\Software\Microsoft\Office\<Version>\UserMRU\LiveID_####\File
 MRU 
