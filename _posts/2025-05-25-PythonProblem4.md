---
title: Detecting Log Volume Spikes with Python
date: 2025-05-25
categories: [DFIR, Python]
tags: [Anomaly Detection, Logs, Python]
author: Harmehar Kaur
image:
  path: /assets/Python_Scripting.jpg
  alt: A visual with python scripting
---

## Catching Spikes in Log Activity with Python

Today was a cool one: building a script that could detect **unusual spikes in log volume** — something you’d totally want to catch in a live environment.

### 🎯 Use Case
- Parse log lines with timestamps
- Count lines per minute or hour
- Alert if log volume doubles or spikes unusually

### 🧪 Sample Log Snippet
May 21 14:01:02 login attempt
May 21 14:01:32 login attempt
May 21 14:03:12 login attempt
... (then suddenly 300 events at 14:04)

pgsql
Copy
Edit

### 📊 Output Sample
| Time Window | Log Count | Spike? |
| ----------- | --------- | ------ |
| 14:01       | 15        |        |
| 14:04       | 312       | ⚠️ Yes  |

### 💡 What I Learned
- Used `datetime.strptime()` to group timestamps
- Stored counts in `dict`
- Compared current vs. average to find anomalies

I see a lot of future use for this kind of script — might even expand it to do alerts via email or Slack.

Tomorrow’s the final one for this week: parsing logs by **severity level** and showing them with color-coded output 🎨

— Harmehar
