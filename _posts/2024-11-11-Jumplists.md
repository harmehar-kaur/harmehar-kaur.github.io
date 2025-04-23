---
title: "Jump Lists in Windows Forensics: Tracking User Activity" 
date: 2024-11-11  
categories: [DFIR]  
tags: [DFIR, Jump Lists, Windows Forensics, User Activity, Recent Files]  
author: Harmehar Kaur  
image:  
  path: /assets/attack.jpg  
  alt: Jump Lists Registry Artifact  
---

Today, let’s dig into another powerful Windows artifact: **Jump Lists**. These are super helpful when you're trying to figure out what files or programs a user recently interacted with.

---

### What are Jump Lists?

Jump Lists are a Windows taskbar feature that gives users quick access to recently or frequently used applications and files. In short, they’re all about enhancing the **user experience and productivity**—but for forensic folks, they offer a goldmine of user activity data.

Think of them as collections of **link files** that point to things the user has opened or interacted with recently.

---

### Where are Jump Lists stored?

You can find Jump List data in two locations within the user’s profile:

- `C:\Users\<Username>\AppData\Roaming\Microsoft\Windows\Recent\AutomaticDestinations`
- `C:\Users\<Username>\AppData\Roaming\Microsoft\Windows\Recent\CustomDestinations`

Let’s break that down:

- **Automatic Destinations**  
  These are stored in a binary CDF format and are more system-controlled. They track Jump Lists used by multiple applications within Windows OS.

- **Custom Destinations**  
  These are application-specific and used by programs to store tailored Jump List info.

---

### Why are Jump Lists useful in DFIR?

From a forensic perspective, Jump Lists can reveal a lot about a user’s behavior, like:

- File paths and tasks accessed
- Timestamps of interaction
- Application details
- User-specific customizations
- Icons and thumbnails associated with files
- Frequency of access (Jump Count)
- Security Identifiers (SIDs)

Applications that commonly use Jump Lists include:

- Microsoft Edge  
- Windows Media Player  
- Microsoft Word, Excel, and PowerPoint  

So if you're reconstructing what a user was doing, when they did it, and what tools they were using—Jump Lists can fill in a lot of those gaps.

---

More artifact breakdowns coming soon. If you're diving into DFIR, Jump Lists are definitely worth getting familiar with!
