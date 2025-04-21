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

Now that I have found my interest in DFIR I would be diving into these a little more in details. FIrst I would be diving into each of the artefacts present in the windows system. 
the topic of interest today is registry artifacts. 

Windows registry is the collection of a database that store system configuration information in 
form of key: value pairs (this information could be about hardware, software or user information 
which could include current user, recently opened files, programs accessed, or devices 
connected). Registry could be viewed by the executing the following utility which allows a user to 
view and edit registry: regedit.exe. This allows a user to access a registry only in a live system.  
▪ Registry Hives: 
• Number of hives: 5 
o DEFAULT  
o SAM  
o SECURITY 
o SOFTWARE  
o SYSTEM   
• Registry hives are the group of keys, subkeys or values stored on the disk these are also 
an artifact used in maximum cases because we cannot work on a live system. Stored in 
the following path: C:\Windows\System32\Config 
220 | H K a u r 
• SAM Hive: 
o SAM Hives store information about the user account, related to logins, or the 
group information. The location at which the above information is stored is 
SAM\Domains\Account\User. 
▪ Registry Keys: 
• There are 5 root keys present in the registry:  
o HKEY_CURRENT_USER is a subkey of HKEY_USERS and stores information about 
root of the configuration of the current user 
o HKEY_USERS: stores all actively loaded user profiles 
o HKEY_LOCAL_MACHINE: stores config information particular to the computer 
o HKEY_CLASSES_ROOT is a subkey of HKEY_LOCAL_MACHINE stores information 
about current programs opened using windows explorer. Stored information is 
also stored under the following keys: 
o HKEY_LOCAL_MACHINE: contains information about the default settings applied 
to all users.  
o HKEY_CURRENT_USER: contains settings that apply to current users 
o HKEY_CURRENT_CONFIG: this key stored information about hardware profile 
used by the local machine  
▪ Registry transaction logs and backups  
• Transaction log is the changelog of the registry hive and are stored as .log files in same 
directory as the hives. These have the current changes which have not yet made their 
way to a hive therefore have a more up-to-date information of the recent activity. 
Backups on the other hand are the opposite of transaction logs. Hives located in the 
config directory are backup every ten days to the following location:  
o C:\Windows\System32\Config\RegBack 
