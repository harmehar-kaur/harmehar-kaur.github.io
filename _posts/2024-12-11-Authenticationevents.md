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
Authentication Events: 
• These identify where an act of authenticating any credentials occurred. These are useful 
while tracking local vs. domain account usage. These records are stored on the system 
where the credentials are authenticated:  
o Local Account/Workgroup = on workstation  
o Domain/Active Directory = on domain controller 
• Win7+: %SYSTEM ROOT%\System32\winevt\logs\Security.evtx Recorded on system that 
authenticated credentials  
• Event ID Codes (NTLM protocol) - 4776: Successful/Failed account authentication  
• Event ID Codes (Kerberos protocol) - 4768: Ticket Granting Ticket was granted 
(successful logon) - 4769: Service Ticket requested (access to server resource) - 4771: 
Pre-authentication failed (failed logon) 
