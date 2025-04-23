---
title: Understanding the Recycle Bin Artifacts in DFIR  
date: 2024-11-25  
categories: [DFIR]  
tags: [DFIR, Forensics, Recycle Bin, Windows]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Recycle Bin Artifacts  
---

In the world of Digital Forensics and Incident Response (DFIR), even something as simple as the **Recycle Bin** can provide important clues. When files are deleted, they don’t necessarily disappear forever. Instead, they often linger in the **Recycle Bin** (or **$Recycle.Bin** on modern systems) until they are permanently removed. These remnants can hold significant evidence, especially in criminal investigations or when analyzing a compromised system.

Let's break down how the **Recycle Bin** stores and handles deleted files across different Windows versions.

---

### Recycle Bin Locations

The **Recycle Bin** is typically a hidden system folder, but it still retains key data on deleted files. The location differs slightly depending on the Windows version:

- **Windows XP**:  
  - `C:\Recycler`

- **Windows 7 and later**:  
  - `C:\$Recycle.Bin`

Each user on the system has a **SID** (Security Identifier) sub-folder inside the **Recycle Bin**. These sub-folders can be mapped to specific users via the registry, providing additional context about who deleted a file.

---

### How Files Are Stored in the Recycle Bin

The **Recycle Bin** behaves differently across versions of Windows. Here’s a breakdown of how deleted files are stored:

- **Windows XP**:  
  - The **INFO2 database** in the **Recycler** folder contains information such as the deletion times and the original filenames of deleted files. This is valuable when trying to track what was deleted and when.

- **Windows 7 and later**:  
  - Files in the **$Recycle.Bin** folder are stored with filenames that begin with **$I######**. These files contain the original filename and the date/time when they were deleted.
  - Files that begin with **$R######** contain the original contents of the deleted file, which can be useful for recovery or forensic analysis.

---

### Why is this Important in DFIR?

For forensic investigators, the **Recycle Bin** offers vital data that can help establish timelines or provide insight into what files a user may have deleted. Whether it’s tracking suspicious activity or piecing together a timeline of events, deleted files are a key source of evidence.

- **Tracking Deletion Events**: The **INFO2 database** (in Windows XP) and **$I######** files (in newer versions) give us timestamps for when files were deleted.
- **Recovering Deleted Data**: The **$R######** files store the original contents of deleted files, which might provide useful information even after the file appears to be gone.
- **Identifying User Behavior**: Since each user has their own **SID** folder, it’s possible to associate deleted files with specific users on the system.

---

### Conclusion

Even though the **Recycle Bin** seems like a simple tool for users to recover deleted files, it can offer powerful insights into a system’s history. For forensic experts, understanding how the **Recycle Bin** works—and where its data is stored—can help uncover important evidence, whether in criminal investigations or internal system audits.

So, next time you’re investigating a system, don’t forget to check the **Recycle Bin**—it might just hold the key to uncovering crucial evidence about deleted files and the actions of the user.

Stay tuned for more forensic tips in **DFIR**!
