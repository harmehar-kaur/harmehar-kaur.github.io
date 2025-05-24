---
title: Web Access Log Analysis in Python
date: 2025-05-23
categories: [DFIR, Python]
tags: [Scripting, Access Logs, HTTP, Analytics]
author: Harmehar Kaur
image:
  path: /assets/Python_Scripting.jpg
  alt: A visual with python scripting
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
```
192.168.1.101 - - [21/May/2025:12:00:02 +0000] "GET /admin HTTP/1.1" 404 512
```

### 📊 Terminal Output Sample
| IP Address    | Requests | 404s | 500s |
| ------------- | -------- | ---- | ---- |
| 192.168.1.101 | 12       | 3    | 0    |

### 🧰 Libraries Used
- `re` for parsing
- `collections` for counting
- `tabulate` for clean output

Let’s take a look at the full script and break it down:

### 💻 The Script

```python
import re
import sys
from collections import defaultdict, Counter
from tabulate import tabulate
import io

ip_counter = Counter()
url_counter = Counter()
error_entries = []

def load_txt(evidence_file):
    """Loads the log file and returns its lines."""
    with open(evidence_file, 'r') as f:
        return f.readlines()

def search_trends(log_lines):
    """
    Parses access logs:
    - Counts total requests per IP
    - Tracks most requested URLs
    - Filters status 500 and 404
    """
    pattern = re.compile(
        r'(?P<ip>\d+\.\d+\.\d+\.\d+)\s-\s-\s\[(?P<timestamp>[^\]]+)\]\s"(?P<method>\w+)\s(?P<url>\S+)\sHTTP/[\d.]+"\s(?P<status>\d+)\s(?P<size>\d+)'
    )

    for line in log_lines:
        match = pattern.search(line)
        if match:
            ip = match.group("ip")
            url = match.group("url")
            status = int(match.group("status"))

            ip_counter[ip] += 1
            url_counter[url] += 1

            if status in (404, 500):
                error_entries.append({
                    "IP": ip,
                    "URL": url,
                    "Status": status,
                    "Timestamp": match.group("timestamp")
                })

def print_results():
    output = io.StringIO()

    def print_section(title, data, headers):
        output.write(f"\n[{title}]\n")
        output.write(tabulate(data, headers=headers, tablefmt="grid") + "\n")

    # Prepare tables
    ip_table = [{"IP": ip, "Requests": count} for ip, count in ip_counter.items()]
    top_ips = ip_counter.most_common(5)
    top_urls = url_counter.most_common(10)

    print_section("Total Requests Per IP", ip_table, "keys")
    print_section("Top 5 IPs by Requests", top_ips, ["IP", "Requests"])
    print_section("Top Requested URLs", top_urls, ["URL", "Hits"])
    print_section("Entries with Status Code 500 or 404", error_entries, "keys")

    # Output to console
    print(output.getvalue())

    # Save to file
    with open("log_report.txt", "w") as f:
        f.write(output.getvalue())

def main():
    if len(sys.argv) != 2:
        print("Usage: python script.py <input_file_path>")
        sys.exit(1)

    filepath = sys.argv[1]
    log_lines = load_txt(filepath)
    search_trends(log_lines)
    print_results()

if __name__ == "__main__":
    main()
```

### 🧠 Let’s Talk Through It

#### `load_txt()`
This function is just opening the provided log file and reading all the lines into memory. Nothing fancy, but it’s foundational.

#### `search_trends()`
Here's the workhorse. It uses a regular expression to:
- Extract each IP, URL, and status code.
- Count how many times each IP and URL appears.
- Record any access logs that result in error codes 404 or 500 — these are the "red flags" we care about.

#### `print_results()`
We structure the output using `tabulate`, split into different sections:
- All IPs and how many requests they made
- Top 5 noisiest IPs
- Most hit URLs
- Error events with timestamps

And just for good measure, we save the results to a `log_report.txt` file as well.

#### `main()`
The usual Python entry point — checks for the right usage, grabs the file path, loads it up, analyzes it, and prints the results.

---

Tomorrow, I’ll explore **file access logs from auditd** — we’re going deeper 🧬


