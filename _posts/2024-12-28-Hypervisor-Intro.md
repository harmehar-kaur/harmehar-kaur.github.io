---
title: 
date: 
categories: 
tags: 
author: 
image:
  path: 
  alt: 
---
after linux systems i also wanted to lay the ground work for hypervisor based systems. there are a scarce amount of resources found out here on hypervisor based vm forensics but i will gather whatever i can get and journal those here. 

1	WHAT ARE HYPERVISORS?
•	A hypervisor is utilized to establish and oversee a virtual computer within a host machine. It generally operates as a lightweight operating system that lacks hardware drivers. The hypervisor manages the allocation of resources needed by each separate virtual machine in real-time by intercepting and simulating all operating system functions within the virtual environment. It efficiently divides and distributes hardware resources, including CPU, memory, and I/O devices.
2	TYPES OF HYPERVISORS
2.1	TYPE 1 HYPERVISORS
•	A type 1 hypervisor runs right on the underlying computer's physical hardware, interacting directly with its central processing unit (CPU), memory and physical storage. 
•	Also referred to as hypervisors as bare-metal hypervisors or native hypervisors. 
•	A type 1 hypervisor takes the place of the host operating system.
•	Has direct access to resources, which makes its performance comparable to that of native execution. 
•	Microsoft’s Hyper-V, Xen, VMware ESXi are some examples of type-I hypervisors that are widely used. 
2.2	TYPE 2 HYPERVISORS
•	A type 2 hypervisor—also referred to as an embedded or hosted hypervisor—doesn't run directly on the underlying hardware. Instead, it runs as an application in an OS. Type 2 hypervisors rarely show up in server-based environments. 
•	They are suitable for individual PC users needing to run different operating systems.
•	Often feature additional toolkits for users to install into the guest OS. These tools provide enhanced connections between the guest and the host OS, usually enabling the user to cut and paste between the two or access host OS files and folders from within the guest VM.
•	Type-II virtualization incurs additional overhead due to the layering of the VMM on top of the host OS when servicing resource requests from VMs. 
•	VMware Workstation/Server/Player, Virtual PC and VirtualBox are some examples of type-II hypervisors widely used on host operating systems. 
