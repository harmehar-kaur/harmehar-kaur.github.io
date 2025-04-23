---
title: "Open/Save and Last Viewed Dialog MRUs: A Forensic Analysis" 
date: 2024-11-24  
categories: [DFIR]  
tags: [DFIR, Forensics, Windows, MRUs]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Open/Save and Last Viewed Dialog MRUs  
---

When investigating user activity on a Windows system, **Open/Save dialogs** and **search queries** provide valuable forensic evidence. Windows keeps track of where files are opened from or saved to, as well as the searches performed in File Explorer. This can offer insight into which files users interacted with and where they were located.

Let's take a look at where this information is stored and how it can be used in forensic investigations.

---

### Open/Save and Last Viewed Dialog MRUs

Windows tracks the locations where files are opened or saved, storing this information in the **NTUSER hive**. These records can be incredibly useful when you need to trace the user's activity. Here’s where you can find these artifacts:

- **Open/Save Location**:  
  - `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePIDlMRU`
  
- **Last Viewed Location**:  
  - `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidlMRU`

These locations record the directories a user has accessed during the **open** or **save** actions, providing a clear trail of where files were handled.

---

### Windows Explorer Address/Search Box

Additionally, Windows stores the paths a user types into the address bar or search box of **Windows Explorer**. This can help you understand what files or locations the user was looking for. The relevant registry keys are located at:

- **Typed Address Path**:  
  - `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPath`
  
- **Search Terms (WordWheelQuery)**:  
  - `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWheelQuery`

---

### WordWheelQuery Explained

The **WordWheelQuery** key maintains an **MRU (Most Recently Used) list** of search terms typed into the **File Explorer search dialog**. These keywords are added in **Unicode** and are listed in temporal order, meaning they are stored based on the order in which the user entered them.

This data can be invaluable in a forensic investigation. By examining the search terms stored in the **WordWheelQuery**, investigators can uncover the user’s interests, files they searched for, and even potential files that they may have intentionally or inadvertently accessed.

---

### Why Does This Matter in Forensics?

The **Open/Save MRUs** and **search history** provide valuable insights into the user’s file handling and search patterns. These entries are often used for:

- **User Activity Tracking**: Correlating actions performed on specific files.
- **Evidence of Interaction**: Identifying what files or locations were accessed.
- **Timeline Construction**: Using timestamps and accessed paths to piece together a timeline of events.

In forensic investigations, these artifacts can help investigators understand user behavior and uncover critical evidence about what was accessed or searched on a system.

---

### Conclusion

In DFIR, the **Open/Save** MRUs and **search queries** in **Windows Explorer** provide essential information for reconstructing user activity. By examining the **NTUSER hive** and associated registry keys, investigators can track file access, uncover search patterns, and establish timelines.

This information is crucial for anyone working to uncover digital evidence during an investigation, and it serves as an important part of the overall forensic process.

Stay tuned for more tips on utilizing **Windows artifacts** in **DFIR** investigations!
