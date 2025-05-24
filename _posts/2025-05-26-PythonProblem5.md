---
title: "Pretty Log Reporting: Errors, Warnings, and Tables"
date: 2025-05-26
categories: [DFIR, Python]
tags: [Log Parsing, Terminal Tables, Pretty Output]
author: Harmehar Kaur
image:
  path: /assets/Python_Scripting.jpg
  alt: A visual with python scripting
  
---

## Pretty Logs, Clean Reports – Filtering by Severity

Last scripting challenge for this week — and one of my favorites: **parsing logs by severity** and displaying them with clean, readable output in the terminal.

### 🎯 What I Wanted to Do
- Search logs for `ERROR`, `WARNING`, `CRITICAL`, etc.
- Print a clean table with color coding
- Keep line numbers and message preview

### 🧪 Sample Log
2025-05-21 13:11:22 ERROR Failed to allocate memory
2025-05-21 13:11:25 WARNING Connection slow

vbnet
Copy
Edit

### 📊 Terminal Table Example
| Line | Level   | Message                   |
| ---- | ------- | ------------------------- |
| 12   | ERROR   | Failed to allocate memory |
| 14   | WARNING | Connection slow           |

### 🖼️ Tools Used
- `rich` library for color-coded output (highly recommend!)
- Regex for matching severity levels
- Script enhancements like command-line args

This one is going to become a reusable component in most of my future scripts — especially for quick log reviews.

---

### 🏁 Wrapping Up

That wraps up my first week of scripting series for DFIR!  
If you're just starting out, I hope these examples help you gain clarity and confidence.

I’ll keep going and dive into more complex cases next — like memory dumps, PCAPs, and maybe even GUI reporting.

Until next time 👋

— Harmehar
