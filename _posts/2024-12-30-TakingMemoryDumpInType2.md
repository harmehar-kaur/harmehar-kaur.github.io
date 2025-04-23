---
title: Taking Memory Dump and Forensic Image of Type 2 Hypervisor
date: 30 December 2024
categories: [DFIR]
tags: [VMware Workstation, Oracle VirtualBox, memory dump, forensic image, type 2 hypervisor]
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: Memory Dump and Forensic Image of Type 2 Hypervisor
---

# Taking Memory Dump and Forensic Image of Type 2 Hypervisor

In this post, we’ll explore how to take memory dumps and create forensic images from Type 2 hypervisor-based virtual machines. These methods can be applied to popular hypervisors like VMware Workstation/Fusion and Oracle VirtualBox.

## VMware Workstation / Fusion

### Memory Dumps

- **Identify the installation directory** of VMware Workstation or Fusion based on your operating system:
  - Windows (32-bit): `C:\Program Files\VMware\VMware Workstation\`
  - Windows (64-bit): `C:\Program Files (x86)\VMware\VMware Workstation\`
  - Linux: `/usr/bin/`
  - Mac OS: `/Library/Application Support/VMware Fusion/`

- **Ensure the vmss2core tool** is available in the directory. If it’s not present, download it from a trusted source like [vmss2core on Archive.org](https://archive.org/).

- **Create a memory dump** using the following commands:
  - For Windows Guest OS: `vmss2core.exe -W virtual_machine_name.vmss virtual_machine_name.vmem`
  - For Windows 8/8.1, Server 2012/2016/2019 Guest OS: `vmss2core.exe -W8 virtual_machine_name.vmss virtual_machine_name.vmem`
  - For Linux Guest OS: `./vmss2core-Linux64 -N virtual_machine_name.vmss`

### Creating Forensic Image

- **Snapshot Creation**:
  - Suspend the VM or take a snapshot to preserve the system’s current state, including disk, memory, and processes.

- **Access Virtual Disk Files**:
  - Locate the VM's `.vmdk` and snapshot files on the host system.
  - Use VMware utilities like `vmware-vdiskmanager.exe` to combine snapshot deltas with base `.vmdk` files into a single virtual disk file if necessary.

- **Convert to Raw Image**:
  - Use forensic tools such as FTK Imager or EnCase to convert `.vmdk` files to raw (`.dd`) format.
    - Example using FTK: `ftkimager.exe <input>.vmdk <output>.dd`
    - Example using EnCase: `encase.exe <input>.vmdk <output>.dd`

- **Verify Integrity**:
  - Calculate and record the MD5 and SHA1 hashes of the original `.vmdk` file and the resulting `.dd` file to ensure no data alteration during conversion.
  - Example: `md5sum <file>` or `sha1sum <file>`

- **Record System Time Skew**:
  - Document the time of both the host and guest operating systems.
  - Check if the guest OS clock is synchronized with the host or an external source, and record any discrepancies.

## Oracle VirtualBox

### Memory Dump

#### Dumping VM Memory to an ELF File

- Use the following command to generate a core dump of the running VM:
  - `$ VBoxManage debugvm <VM_Name> dumpvmcore --filename=<Output_File_Name>.elf`
  - Replace `<VM_Name>` with the name of the running VM and `<Output_File_Name>` with your desired file name.
  - Example: `$ VBoxManage debugvm Win7 dumpvmcore --filename=Win7.elf`

#### Identifying the Memory Section in the ELF File

- To locate the memory section in the ELF file, run:
  - `$ objdump -h <Output_File_Name>.elf | egrep -w (Idx|load1)`

#### Extracting the Memory Dump

- Use the size and offset values to extract the memory dump:
  - `$ size=0x<SIZE_FROM_OBJDUMP>`
  - `$ off=0x<OFFSET_FROM_OBJDUMP>`
  - `$ head -c $(($size+$off)) <Output_File_Name>.elf | tail -c +$(($off+1)) > <Output_File_Name>.raw`

#### Analyzing the Memory Dump with Volatility

- Run the following command to analyze the memory image:
  - `$ python vol.py -f <Memory_File>.raw imageinfo`
  - Example: `$ python vol.py -f Win7.raw imageinfo`
  - This command outputs suggested profiles and other useful details for further analysis.
