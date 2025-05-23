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
```
May 21 11:23:45 kali sshd[1213]: Failed password for invalid user admin from 192.168.1.10 port 55432 ssh2
```

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

The script followed a set pattern: load the file, search for the required text, and then display the results. For the script, you can move to the GitHub repository where I will be updating the scripts daily.

Let me explain the script first:

I used libraries like `sys`, `re`, `tabulate`, and `defaultdict` for reading files, displaying results, and managing data cleanly.

### 💻 The Script

```python
import sys
import re
from collections import defaultdict
from tabulate import tabulate

# Global variable to hold the log lines
log_lines = []

# Load the log file
def load_file(evidence_file_path):
    global log_lines
    try:
        with open(evidence_file_path, 'r') as file:
            log_lines = file.readlines()
    except FileNotFoundError:
        print(f"[ERROR] File not found: {evidence_file_path}")
        sys.exit(1)

# Search for failed SSH logins
def search_pattern():
    failed_attempts = []

    pattern = re.compile(
        r'^(?P<timestamp>\w{3}\s+\d{1,2}\s[\d:]+)\s.*sshd\[\d+\]:\sFailed password for (invalid user )?(?P<user>\w+) from (?P<ip>\d{1,3}(?:\.\d{1,3}){3})'
    )

    for line in log_lines:
        match = pattern.search(line)
        if match:
            failed_attempts.append({
                'timestamp': match.group("timestamp"),
                'username': match.group("user"),
                'ip': match.group("ip")
            })

    return failed_attempts

# Display results
def print_results():
    failed_logins = search_pattern()
    attempts_by_ip = defaultdict(int)

    detailed_table = []
    for attempt in failed_logins:
        detailed_table.append([
            attempt['timestamp'],
            attempt['ip'],
            attempt['username']
        ])
        attempts_by_ip[attempt['ip']] += 1

    # Print detailed failed attempts
    print("\n=== Failed SSH Login Attempts ===\n")
    print(tabulate(detailed_table, headers=["Timestamp", "IP Address", "Username"], tablefmt="grid"))

    # Summary by IP
    summary_table = [[ip, count] for ip, count in attempts_by_ip.items()]
    print("\n=== Summary: Total Failed Attempts by IP ===\n")
    print(tabulate(summary_table, headers=["IP Address", "Failed Attempts"], tablefmt="grid"))

# Main 
def main():
    if len(sys.argv) < 2:
        print("Usage: python Suspicious_logins.py <path to file>")
        sys.exit(1)

    evidence_file_path = sys.argv[1]
    load_file(evidence_file_path)
    print_results()

if __name__ == "__main__":
    main()
```

### 🔍 Let's Break It Down

#### `load_file()`
This function takes the path to the log file (provided by the user) and reads all lines into a global list. If the file doesn’t exist, we gracefully exit with an error message.

#### `search_pattern()`
Here’s where the magic of regex happens. This function scans each log line for a pattern that matches a failed SSH login. It captures:
- The timestamp
- The username (even if it's an "invalid user")
- The source IP

Each match is saved in a dictionary and added to a list of failed attempts.

#### `print_results()`
We take the list of failed login attempts and:
1. Display a detailed list (with timestamps) in a grid format.
2. Summarize the total number of attempts per IP address.

We use `tabulate` here to make everything neat and readable.

#### `main()`
This is the entry point. It ensures the user supplies a file path and then kicks off the loading and processing of the log.

---

Tomorrow, I’ll move to **web server log analysis** — parsing access logs like a pro 🕵️‍♀️.

Stay tuned!
