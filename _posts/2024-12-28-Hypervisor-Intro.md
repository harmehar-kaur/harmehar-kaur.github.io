---
title: "Getting Started with Hypervisor-Based VM Forensics"
date: 2024-12-28
categories: [DFIR]
tags: [hypervisor, virtualization, vm forensics, type 1 hypervisor, type 2 hypervisor]
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: hypervisor-based forensics
---

After exploring Linux systems, I wanted to start laying the groundwork for hypervisor-based systems. There’s a real scarcity of accessible resources out there for hypervisor-based VM forensics, but I’ll gather whatever I can and journal my findings here. Let's break it down.

## What Are Hypervisors?

- A hypervisor is used to create and manage virtual machines (VMs) on a host system. Think of it as a lightweight operating system that doesn't need hardware drivers itself.
- It simulates and manages hardware access for each virtual machine by intercepting and emulating operating system-level calls.
- It divides up physical system resources — CPU, memory, I/O — and distributes them in real-time to virtual machines.

## Types of Hypervisors

### Type 1 Hypervisors

- **Also known as bare-metal or native hypervisors**, these run *directly* on the host hardware.
- They don't require a host OS and instead act as the base operating environment.
- Since they have direct access to hardware, performance is usually close to native execution.
- Some common examples include:
  - Microsoft Hyper-V
  - Xen
  - VMware ESXi

### Type 2 Hypervisors

- Also called **hosted hypervisors**, these run *on top* of an existing operating system.
- They're more suited for desktop and experimental use rather than production servers.
- These hypervisors often come with toolkits that enhance interaction between guest and host systems — like sharing clipboard or file systems.
- However, there's an extra performance cost due to the layering of the host OS.
- Common examples include:
  - VMware Workstation / Server / Player
  - VirtualBox
  - Virtual PC
