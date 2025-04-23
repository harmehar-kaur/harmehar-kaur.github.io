---
title: Taking Memory Dump and Forensic Image of Type 1 Hypervisor
date: 29 December 2024
categories: [DFIR]
tags: [VMware ESXi, Hyper-V, XenServer, RHEV, memory dump, forensic image, type 1 hypervisor]
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: Memory Dump and Forensic Image of Type 1 Hypervisor
---

# Taking Memory Dump and Forensic Image of Type 1 Hypervisor

In this post, we'll dive into the methods for taking memory dumps and creating forensic images from Type 1 hypervisors. These techniques are particularly useful for hypervisors like VMware ESXi, Hyper-V, XenServer, and RHEV. Let’s get started!

## VMware ESXi / vSphere

### Memory Dump

- **Start an SSH session** to the ESXi host and identify the VM's world ID using:
  - `vm-support -x`
  - For ESXi 6.7 and above, use: `esxcli vm process list`
  
- **Suspend the VM** using:
  - `vm-support -Z world_ID`
  
- **Copy the .vmss and .vmem files** to the machine running `vmss2core`.
  
- **Run `vmss2core`** with the appropriate options to create the memory dump.

### Creating Forensic Image

- **Snapshot Creation**:
  - Suspend the VM or take a snapshot to preserve the system's current state, including disk, memory, and processes.

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

## Hyper-V

### Memory Dump

- Use the `vm2dmp.exe` utility to create memory dumps from Hyper-V virtual machine state files:
  - Example: 
    - `vm2dmp.exe -bin C:\dir\VM-Instance-ID.bin -vsv C:\VM\VM-Instance-ID.vsv -dmp C:\dir\crashdump.dmp`
  
- **Create a dump file** from the VM name and snapshot:
  - Example: 
    - `vm2dmp.exe -vm VMName -dmp C:\VM\crashdump.dmp`
    - `vm2dmp.exe -vm VMName -snap vm VMName -snap-SP1 -dmp C:\VM\crashdump.dmp`

- Optionally, specify debugging symbols path using the `-sym` flag.

### Forensic Image

- To take a snapshot of a virtual machine's memory in Hyper-V, use the **Checkpoint** functionality, either via the Hyper-V Manager or PowerShell.
  
- Before creating the checkpoint, ensure the VM has checkpoints enabled, and they are configured as **Standard checkpoints**, rather than **Production**. This ensures that the current state of applications is captured.
  
- **Creating a Checkpoint**:
  - **Hyper-V Manager**: Locate the appropriate VM, right-click, and select **Checkpoint**.
  - **PowerShell**: Use the `Checkpoint-VM` command and pass in the VM name:
    - `PS > Checkpoint-VM -Name [VMName]`
  - This will instruct Hyper-V to take the checkpoint.

## Xen/Citrix XenServer

### Using the xeCLI

- Open a text console or SSH session to the XenServer host.
  
- **Obtain the domain ID** of the VM:
  - `xe vm-param-get uuid=<vm_uuid> param-name=dom-id`
  
- **Trigger an NMI** to force a crash dump:
  - `xl trigger <dom_id> nmi`
  
- **Verify the creation** of the memory dump file in the configured location after the VM restarts.

### Using XenCenter

- **Enable manual crash dumps** in the guest OS (e.g., CrashOnCtrlScroll registry key for Windows).
  
- **Trigger the crash dump** using the keyboard shortcut `Ctrl+Scroll Lock+Scroll Lock` in the VM console.

- Ensure that **XenCenter console options** do not interfere with keyboard shortcuts.

### OVA Extraction and Analysis

#### What is OVA?

- An **Open Virtualization Archive (OVA)** is a compressed file containing the virtual machine’s disk and metadata, typically provided by the Citrix XenServer.

#### Procedure for OVA Extraction

- Open the OVA file using a **zip extraction utility**.
  
- Extract the contents, including **VMDK, MF, and OVF** files.
  
- **Convert the VMDK file** to other formats (e.g., VHD) for compatibility with other virtualization platforms.

#### Precautions

- The virtual machine **must remain offline** during the procedure.
  
- Ensure that **all artifacts are hash-verified** for integrity.

## RHEV

### Memory Dumps

- **Verify Virtual Machine Configuration**:
  - Identify the virtual machine you need to investigate.
  - Check its allocated memory using the following command:
    - `$ oc get vm <vm_name> -o yaml | grep memory`
    - Example output: `memory: 4Gi`
    - Note: The allocated memory size impacts the time required to create and download the dump.

- **Create a Memory Dump**:
  - Use the `virtctl memory-dump` command to generate the memory dump:
    - `$ virtctl memory-dump get <vm_name> --create-claim --claim-name=<vm_name>-mem --output=<output_file_name>.tar.gz`
    - Replace `<vm_name>` with the virtual machine's name and `<output_file_name>` with the desired output file name.

- **Verify the memory dump** file integrity using hashing algorithms (e.g., MD5, SHA256):
  - `$ sha256sum <output_file_name>.tar.gz`

### Forensic Images

- **Identify Virtual Disk**:
  - Locate the virtual disk associated with the VM using the **RHEV Manager** interface or CLI commands:
    - `$ lvs | grep <vm_name>`

- **Create a Forensic Image**:
  - Use imaging tools to create a bit-by-bit copy of the virtual disk:
    - For `dd`: `$ dd if=/dev/<disk_path> of=<output_file>.dd bs=4M status=progress`
    - For **FTK Imager**: 
      - Select the disk as the source.
      - Choose the desired output format (e.g., `.E01`, `.dd`).

- **Verify the forensic image** integrity:
  - `$ sha256sum <output_file>.dd`

- **Store the forensic image** on a write-protected medium for further analysis.
