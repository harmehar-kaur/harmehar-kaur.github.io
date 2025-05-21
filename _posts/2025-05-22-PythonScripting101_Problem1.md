---
title: Detecting Suspicious SSH Logins with Python
date: 2025-05-22
categories: [DFIR, Python]
tags: [Scripting, SSH, Logs, Security]
author: Harmehar Kaur
---

## Detecting Suspicious SSH Logins with Python

Today I tackled my first scripting challenge: **parsing SSH authentication logs** to detect suspicious login attempts.

The goal was simple but very real-world: go through an `auth.log` file (or even a `.gz` one), pull out all the **failed SSH login attempts**, and summarize them by IP address. 

This is something that would be buried in pages of logs if you were using `cat`, but Python gives us structure and clarity.

### 🎯 What I Needed to Extract
- Timestamp
- Username (or "invalid user")
- Source IP
- Number of failed attempts per IP

### 🧪 Sample Log Line
May 21 11:23:45 kali sshd[1213]: Failed password for invalid user admin from 192.168.1.10 port 55432 ssh2


### 📊 Output Format (Terminal Table)
| IP Address   | Username | Attempt Count |
| ------------ | -------- | ------------- |
| 192.168.1.10 | admin    | 3             |
| 192.168.1.11 | test     | 1             |

### 🧰 Tools Used
- Python's `re` module for parsing
- `collections.Counter` to count attempts
- `tabulate` to make it look clean in the terminal

This script was simple but powerful. I could even add logic later to **alert if an IP crosses a threshold**, or export the report for a manager.

Tomorrow, I’ll move to **web server log analysis** — parsing access logs like a pro 🕵️‍♀️.

Stay tuned!

— Harmehar
