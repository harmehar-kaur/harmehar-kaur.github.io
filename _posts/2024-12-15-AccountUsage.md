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
Account usage: 
o Cloud account details:  
▪ Microsoft Cloud Accounts store account information in the SAM hive, including the email 
address associated with the account. Location  
▪ SAM\Domains\Account\Users\\InternetUserName  
▪ InternetUserName value contains the email address tied to the account. The presence of this 
value identifies the account as a Microsoft cloud account  
o Last Login and Password Change  
▪ The SAM registry hive maintains a list of local accounts and associated configuration 
information.  
▪ SAM\Domains\Account\Users  
▪ Accounts listed by their relative identifiers (RID) Last login time, last password change, login 
counts, group membership, account creation time and more can be determined  
o User access logging  
▪ this included in windows server version from 2012 and later. This is used to identify things like 
user access and system-related statistical data in near real-time. User Access Logging is a feature 
included with server versions of Microsoft Windows, enabled on Windows Server System 2012 
and later. It collects user access and system-related statistical data in near real-time.  
▪ The data is stored in the directory `C:\Windows\System32\LogFiles\SUM\`, which contains files 
such as `SystemIdentity.mdb` or `Current.mdb` along with one or more GUID-based files that 
should exist in this location. The feature tracks the active UAL database, which contains basic 
server configuration information. Data from this database is copied to ending `.mdb` files. It 
236 | H K a u r 
retains data from the current year, the previous year, and up to two years prior, while archived 
events are retained for 24 hours.  
▪ Additionally, the IP address is tracked to identify the location from which associated activity 
originated, while the destination is the system from which UAL was obtained. This tracking 
capability can be used to identify abnormal access to systems and profile lateral movement from 
various clients to servers.  
▪ The system records the UTC timestamp of the first access for the year (InsertDate) for a specific 
user, including details such as the source IP and role. It also captures the UTC timestamp of the 
last access for the year (LastAccess).  
▪ The logging feature is closely associated with file servers and SMB access.  User Access Logging is 
designed to provide system administrators with insights into server usage on Windows servers. 
It maintains a detailed record of the types of services accessed on a server, the usernames 
associated with access, and the source IP addresses from which the access occurred. 
