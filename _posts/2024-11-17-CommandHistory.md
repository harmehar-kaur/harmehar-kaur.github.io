---
title: "Command History: Tracking Run Dialog Commands in Windows"  
date: 2024-11-17  
categories: [DFIR]  
tags: [DFIR, Command History, MRU, Windows Artifacts, Run Dialog]  
author: Harmehar Kaur  
image:  
  path: /assets/attack.jpg  
  alt: Command History in DFIR  
---

In this post, we’re diving into another important Windows artifact: **Command History**. Specifically, we’ll be looking at the history of commands executed through the **Run Dialog**.

---

### What is Command History?

Every time a user runs a command from the **Run Dialog** (you know, pressing `Win + R`), Windows keeps track of those commands. This record can provide valuable insights into what the user has been doing on the system, which can be critical during a forensic investigation.

The **Command History** is stored in the registry under the following location:

- `NTUSER\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU`

---

### What does the history include?

The **RunMRU** key is an **MRU (Most Recently Used)** list, meaning it tracks commands in the order they were executed. This is stored in a temporal order via the **MRUList** key, showing which commands the user most recently executed in the **Run Dialog**.

---

### Why is Command History important?

Command history can give us a glimpse into what the user was doing or trying to do. This could be helpful for understanding the user’s intent or the actions that led up to a certain event. It’s also valuable for tracking down **executed programs**, **file paths**, or even **malicious commands** if you’re investigating a potential breach.

While the RunMRU list might not be the first artifact you look at, it’s always a good idea to check when you’re building a timeline of user actions.

Stay tuned for more posts about Windows artifacts and how they can help with DFIR investigations!
