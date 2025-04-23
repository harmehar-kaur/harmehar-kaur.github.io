---
title: "Memory Dumping on Linux Using LiME"
date: 2024-12-27
categories: [DFIR]
tags: [linux forensics, memory dumping, LiME, volatility, kernel module]
author: harmehar kaur
image:
  path: /assets/forensics.jpg
  alt: Linux memory dumping using LiME
---

# Memory Dumping on Linux Using LiME

If you're diving into memory forensics on a Linux system, **LiME** (Linux Memory Extractor) is one of the most effective tools at your disposal. It’s especially handy when you need a forensically sound method to grab a full memory image from a live system — including Android devices. Let’s walk through how to get started with LiME and use it for memory dumping.

## What is LiME?

LiME is an open-source **Loadable Kernel Module (LKM)** that allows you to capture a complete memory image from Linux and Linux-based systems. It’s built to minimize interaction between user and kernel space, making its captures more reliable and tamper-resistant compared to other tools.

---

## Collecting Memory Dumps with LiME

### 🛠 Prerequisites

Make sure you’ve got the necessary tools installed:

- **Git**: To clone the LiME repository.
- **Build-essential**: Needed for compiling the module.
- **Linux Kernel Headers**: Required for building kernel modules.

```bash
sudo apt update
sudo apt install git build-essential linux-headers-$(uname -r)
```

---

### 📥 Clone the LiME Repository

```bash
git clone https://github.com/504ensicsLabs/LiME.git
cd LiME
```

---

### 🧱 Compile the LiME Module

```bash
cd src
make
```

> After compiling, you should see a `lime.ko` file in the `src` directory.

---

### 🚀 Load the LiME Module

You can save the memory dump locally or send it over a network.

#### 💾 Save Locally

```bash
sudo insmod lime.ko path=/path/to/dump.mem format=raw
```

- This will save a `.mem` file in your specified directory.

#### 🌐 Save Over a Network

```bash
sudo insmod lime.ko path=tcp:192.168.1.2:4444 format=lime
```

- Replace `192.168.1.2` with your target system's IP address and `4444` with your desired port.

---

### 🔍 Verify the Memory Dump

- **If saved locally:**

```bash
ls -lh /path/to/
```

- **If sent over a network:**

Make sure the receiving system is listening with `netcat`:

```bash
nc -l -p 4444 > memory_dump.lime
```

---

### 🔄 Unload the LiME Module (Optional)

Once you're done collecting the memory image, you can unload LiME like so:

```bash
sudo rmmod lime
```

---

LiME is a powerful tool that helps maintain forensic integrity while performing live memory acquisition on Linux systems. Whether you’re investigating an incident or doing routine checks, adding it to your toolkit is a no-brainer.
