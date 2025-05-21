---
title: Web Access Log Analysis in Python
date: 2025-05-23
categories: [DFIR, Python]
tags: [Scripting, Access Logs, HTTP, Analytics]
author: Harmehar Kaur
---

## Analyzing Web Server Access Logs with Python

Today’s task was a deep-dive into **web server access logs** — the kind you’d see from Apache or Nginx.

These logs are gold mines for detecting anomalies like:
- Suspicious IPs
- 404/500 errors
- Repeated access to admin endpoints

### 🎯 What I Extracted
- Requesting IP
- Requested URL
- HTTP Status code
- Top IPs and top URLs

### 🧪 Sample Log Line
192.168.1.101 - - [21/May/2025:12:00:02 +0000] "GET /admin HTTP/1.1" 404 512

markdown
Copy
Edit

### 📊 Terminal Output Sample
| IP Address    | Requests | 404s | 500s |
| ------------- | -------- | ---- | ---- |
| 192.168.1.101 | 12       | 3    | 0    |

### 🧰 Libraries Used
- `re` for parsing
- `collections` for counting
- `tabulate` for clean output

Tomorrow, I’ll explore **file access logs from auditd** — we’re going deeper 🧬

— Harmehar
