---
title: Creating Forensic Images on Linux Using the dd Command  
date: 2024-12-26  
categories: [DFIR]  
tags: [Linux Forensics, Forensic Imaging, dd Command, Disk Imaging, Incident Response]  
author: Harmehar Kaur  
image:  
  path: /assets/forensics.jpg  
  alt: Forensic Imaging in Linux using dd  
---

When performing digital forensics on a Linux system, one of the most fundamental steps is to create a bit-for-bit copy of the disk—also known as a **forensic image**. One of the most trusted tools for this task is the built-in `dd` command. It's straightforward, flexible, and available on almost every Unix-like system.

In this post, I’ll walk you through how to create a forensic image using `dd` (and a few variants like `dcfldd` and `dc3dd`), ensuring your evidence remains intact and verifiable.

---

### 🔍 Getting Started: Identify Your Target Disk

Before you image anything, you need to know what you’re imaging.

- **List all block devices** to find your target disk:
  ```bash
  lsblk
  ```

- **Check partition layout and details:**
  ```bash
  fdisk -l
  ```

This helps you confirm the correct device path (e.g., `/dev/sdb`) and avoid accidental overwrites.

---

### 💾 Creating the Forensic Image with `dd`

Once you’ve identified the disk, you can use the `dd` command to create the image:

```bash
dd if=/dev/sdb of=/path/to/external/device/image.img status=progress
```

- `if=` is the input file (your source disk).
- `of=` is the output file (your image location).
- `status=progress` gives you real-time feedback during imaging.

---

### ✅ Verifying Integrity with Hashing

To ensure the integrity of your forensic image, you should generate a cryptographic hash:

```bash
md5sum /path/to/external/device/image.img > imagemd5.md5
```

This hash can later be used to verify that the image hasn’t been altered.

---

### 🔒 Alternative Tools: `dcfldd` and `dc3dd`

While `dd` works fine, there are enhanced versions with built-in hashing capabilities:

- **Using `dcfldd`:**
  ```bash
  dcfldd if=/dev/sdb of=/destination/image.img hash=md5 hashwindow=1M hashlog=/destination-folder/file.hash status=on
  ```

- **Using `dc3dd`:**
  ```bash
  dc3dd if=/var/log/messages of=/tmp/dc3dd hash=sha512
  ```

These tools let you hash while imaging, which is ideal in time-sensitive or forensic environments.

---

### 🛡️ Final Tips

- Always image to an external device—not the source system’s own partitions.
- Validate your hashes both before and after analysis.
- Document everything (commands used, hashes, device IDs, timestamps) for your forensic chain of custody.

Forensic imaging is a critical step in digital investigations, and doing it right ensures the data remains trustworthy for analysis—or even court.
