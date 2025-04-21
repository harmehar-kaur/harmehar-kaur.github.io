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
Browser artifacts: 
• Browser artifacts are useful for profiling user activity on the system under investigation 
or system of interest. Information that could be of interest to the investigators and is 
stored in browsers are cookies, history, cache, session information and other config 
information. This is stored in an SQLite database. Cache is stored in directory named 
cache present in the below mentioned locations. Location of these could vary based on 
chromium-based browsers: 
o Microsoft Edge: %LocalAppData%\Microsoft\Edge\UserData\ 
[Default|ProfileX]\* 
o Google Chrome: %LocalAppData%\Google\Chrome\User Data\Default\* 
o Mozilla Firefox: %AppData%\Mozilla\Firefox\Profiles\xxxxxxxx.default-release\* 
