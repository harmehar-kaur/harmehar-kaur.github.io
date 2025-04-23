---
title: Internet Explorer History in DFIR  
date: 2024-12-03  
categories: [DFIR]  
tags: [DFIR, Forensics, Internet Explorer, History Database]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Internet Explorer History  
---

When diving into **Digital Forensics and Incident Response (DFIR)**, one of the valuable sources of user activity data is the **Internet Explorer History database**. This database holds records about the files accessed locally and remotely, providing crucial evidence for investigators. Even on newer systems where **Internet Explorer** is no longer the default browser, remnants of this history can still be found. Let’s take a closer look at where to find these artifacts and what they can reveal.

---

### What Can Internet Explorer History Tell Us?

Internet Explorer’s history stores access details on files, both local and remote. This gives investigators insight into files that were opened on the system, especially useful for understanding a user’s actions and potential timeline during an investigation. However, this doesn’t tell you if a file was accessed through the browser—just that the file was interacted with in some form.

---

### Where Is the Internet Explorer History Stored?

The location of the history databases varies depending on the version of **Internet Explorer** and the operating system. Here's where you can find these databases:

- **Internet Explorer (IE6–7)**:  
  `C:\Users\<Username>\LocalSettings\History\History`

- **Internet Explorer (IE5, IE8–9)**:  
  `C:\Users\<Username>\AppData\Local\Microsoft\Windows\History\History`

- **Internet Explorer (IE5, IE10–11) & Windows 10+**:  
  `C:\Users\<Username>\AppData\Local\Microsoft\Windows\WebCache\WebCacheV*.dat`

---

### What Information Is Stored?

The records in the **Internet Explorer History** database are typically stored as entries in the following format:  
`file:///C:/directory/filename.ext`

- These entries can help investigators identify files accessed on the system.
- They can also be used to track remote or local files that were opened.

For **deleted items** or files that no longer exist, entries may still appear with the following format:  
`file:///C://`

---

### Why Does This Matter in DFIR?

Even with the rise of other browsers, **Internet Explorer History** can still provide useful evidence, especially when the system is older or when remnants of the browser's history remain on newer systems. While it doesn't explicitly tell you if a file was opened within the browser, it provides key indicators of which files were accessed, giving investigators a starting point in tracing user activity.

This history can be critical when trying to understand the context of a file's existence and its access timeline, especially in the context of potential cover-ups or deletions.

---

### Conclusion

In **DFIR investigations**, even seemingly mundane artifacts like **Internet Explorer History** can provide vital clues about user activity. It’s always worth checking these databases to see what files were accessed, even if Internet Explorer isn't actively used. With the right tools and knowledge, this often-overlooked data can contribute significantly to a thorough investigation.

