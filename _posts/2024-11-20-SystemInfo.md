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
System Configuration 
▪ OS: 
▪ OS version is stored at the location: SOFTWARE\Microsoft\Windows NT\CurrentVersion  
▪ Control Sets: 
▪ Control sets are the hives that store the configuration data of the machine used to control 
system startup. There are commonly 2 control sets which are present in the SYSTEM hive and are 
ControlSet001(commonly is the control set machine used to boot with) and ControlSet002(stores 
the last known good configuration). Other than the above mentioned 2 there is a volatile control 
224 | H K a u r 
set, which is called CurrentControlSet and is used to get the most current and accurate system 
information in case of a live system. The disk location of this is SYSTEM\Select\Current. The ‘last 
known good’ configuration could also be found using registry value: 
SYSTEM\Select\LastKnownGood 
▪ Computer Name: 
▪ Computer name: this is used to confirm that we are working on the correct machine. This could 
be found at the SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName 
▪ Time Zone Information: 
▪ Time zone information helps us establish an understanding of the current time of the local 
machine and the standard times. Which help in understanding the timestamps found on several 
media or files and facilitate the theorizing of a timeline of events. This is stored at 
SYSTEM\CurrentControlSet\Control\TimeZone\Information 
▪ Network Interfaces: 
▪ Network interfaces and past networks are useful in case of finding information like IP addresses, 
DHCP IP addresses subnet mask, DNS servers etc. these are located at the following: 
• SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces 
• SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signature\Unmanaged 
• SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signature\Managed 
