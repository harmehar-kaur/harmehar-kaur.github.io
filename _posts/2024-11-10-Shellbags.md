---
title: Investigating Shellbags in Windows Forensics  
date: 2024-11-10  
categories: [DFIR]  
tags: [DFIR, Shellbags, Windows Registry, User Activity, Forensics]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Shellbags Registry Artifact  
---

Let’s talk about **Shellbags**—a lesser-known but incredibly useful artifact in Windows forensics.

---

### What are Shellbags?

Shellbags store information about the **folder view preferences** a user has set while browsing folders on the system. This includes things like:

- View layout (details, icons, list, etc.)
- Window size and position
- Sorting and grouping preferences

Basically, any time a user opens a folder and tweaks the view settings, Windows logs that behavior using Shellbags.

---

### Why do Shellbags matter in DFIR?

From a forensic point of view, Shellbags can help answer questions like:

- Which folders did the user access?
- Were folders opened from external devices or hidden paths?
- When was a folder last interacted with?

Even if the folders themselves no longer exist, the Shellbag entries may still remain—making them a powerful source of historical data.

---

### Where are Shellbags stored?

You’ll find Shellbag data in two key user registry hives:

#### In `USRCLASS.DAT`:
- `LocalSettings\Software\Microsoft\Windows\Bag`
- `LocalSettings\Software\Microsoft\Windows\BagMRU`

#### In `NTUSER.DAT`:
- `Software\Microsoft\Windows\Shell\Bag`
- `Software\Microsoft\Windows\Shell\BagMRU`

These hives are user-specific, so each profile will have its own Shellbag data.

---

If you're trying to build a timeline of user activity or uncover traces of accessed directories—especially ones that no longer exist—Shellbags are definitely something you should be digging into.

More artifact breakdowns coming soon. Stay tuned!
