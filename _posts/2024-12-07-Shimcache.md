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
ShimCache:  
• is also called as application compatibility cache or AppCompatCache and is a mechanism 
for keeping track for application compatibility with OS and also tracks all application 
launched on the machine. The information recorded here is executive file name, path, 
and timestamp (last modification time of the file). Is not evidence of execution in 
windows 10 or later. Renaming or moving a file causes the file to be re-shimmed. This 
retains last 1024 entries. “Evidence of presence” in windows 10 or higher while it was 
considered evidence of execution prior to windows 10.  These are only written on 
reboot or shutdown. In simple words these helps ensure backward compatibility of 
application. We can use AppCompatParser also a Zimmerman tool which works as 
follows:  
Input: SYSTEM 
hive 
Parses
 Output: CSV 
file
 • This cache gives us information like file size, file location, last modifed time and 
executables. Located in SYSTEM hive. 
o SYSTEM\CurrentControlSet\Control\SessionManager\AppCompatCach
