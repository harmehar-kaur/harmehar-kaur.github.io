---
title: File Access Tracking with Linux Audit Logs
date: 2025-05-24
categories: [DFIR, Python]
tags: [Auditd, Log Analysis, Python, Linux]
author: Harmehar Kaur
---

## Who Accessed What? Tracking File Access in Logs

Today I worked with something a bit more raw: **Linux audit logs** — specifically, logs from `auditd`.

This is super useful when trying to figure out **who accessed sensitive files** like `/etc/passwd`.

### 🎯 Goals for the Script
- Parse logs for `SYSCALL` or `OPEN` events
- Extract file path, UID/username, and timestamp
- Only show specific files of interest

### 🧪 Sample Log Line
type=SYSCALL msg=audit(1629472345.222:317): ... name="/etc/passwd"

pgsql
Copy
Edit

### 📊 Terminal Report
| File Path   | UID  | Access Type | Timestamp           |
| ----------- | ---- | ----------- | ------------------- |
| /etc/passwd | 1000 | read        | 2025-05-21 13:12:01 |

### 🔧 Extra Steps
- Used `datetime.fromtimestamp()` to convert timestamps
- Handled long lines and log splitting
- Mapped UID to user (optional but useful)

This was a more realistic forensic analysis problem — and I’m loving the challenge.

Tomorrow: **detecting anomalies in log volume over time**.

Let’s go 🔍

— Harmehar
