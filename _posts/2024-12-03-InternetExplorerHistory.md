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
Internet Explorer History: 
• Internet Explorer History databases hold information on the local and remote file access 
which provides investigators with means for determining things like files accessed on the 
system, per user. 
• Information can be present even on Win11+ systems missing the Internet Explorer 
application.  
• Location:  
o Internet Explorer: IE6–7: %USERPROFILE%\LocalSettings\History\History 
o IE5 IE8–9: %USERPROFILE%\AppData\Local\Microsoft\Windows\History\History 
o IE5 IE10–11 & Win10+: 
%USERPROFILE%\AppData\Local\Microsoft\Windows\WebCache\WebCacheV*.
 dat  
• Entries recorded as: file:///C:/directory/filename.ext 
• This doesn’t give us information about a file being opened in the browser  
• For deleted items and file that existed: Entries are recorded as: file:///C:// 
