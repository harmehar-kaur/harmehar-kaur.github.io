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
Open/Save and last viewed dialog MRUs:  
• windows remember the location at which a file is either saved at or opened to. The 
location of it is saved in the following location in the NTUSER hive.  
227 | H K a u r 
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32
 \OpenSavePIDlMRU 
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32
 \LastVisitedPidlMRU 
 Windows explorer address/search box:  
• the path a user may have types in the address bar or the searches they must have 
carried out in the search box of a windows explorer are also stored in the NTUSER hive 
at the following location:  
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPat
 h 
o NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWhe
 elQuery 
• WordWheelQuery: This maintains an ordered list of terms put into the File Explorer 
search dialog. Keywords are added in Unicode and listed in temporal order in an MRUlist
