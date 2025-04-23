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
3	TAKING MEMORY DUMP AND FORENSIC IMAGE OF TYPE 1 HYPERVISOR 
3.1	VMWARE ESXI / VSPHERE
3.1.1	Memory Dump
•	Start an SSH session to the ESXi host and identify the VM's world ID using: 
o	vm-support -x
o	For ESXi 6.7 and above, use: esxcli vm process list
•	Suspend the VM using: 
o	vm-support -Z world_ID
•	Copy the. vmss and .vmem files to the machine running vmss2core.
•	Run vmss2core with the appropriate options to create the memory dump.
3.1.2	Creating forensic image 
•	Snapshot Creation:
o	Suspend the VM or take a snapshot to preserve the system's current state, including disk, memory, and processes.
•	Access Virtual Disk Files:
o	Locate the VM's .vmdk and snapshot files on the host system.
o	Use VMware utilities like vmware-vdiskmanager.exe to combine snapshot deltas with base .vmdk files into a single virtual disk file if necessary.
•	Convert to Raw Image:
o	Use forensic tools such as FTK Imager or EnCase to convert .vmdk files to raw (.dd) format.
o	Example using FTK: ftkimager.exe <input>.vmdk <output>.dd
o	Example using EnCase: encase.exe <input>.vmdk <output>.dd
•	Verify Integrity:
o	Calculate and record the MD5 and SHA1 hashes of the original .vmdk file and the resulting .dd file to ensure no data alteration during conversion.
o	Example: md5sum <file> or sha1sum <file>
•	Record System Time Skew:
o	Document the time of both the host and guest operating systems.
o	Check if the guest OS clock is synchronized with the host or an external source, and record any discrepancies.
3.2	HYPER-V
3.2.1	Memory Dump
•	Use the vm2dmp.exe utility to create memory dumps from Hyper-V virtual machine state files: 
o	Example: 
	vm2dmp.exe -bin C:\dir\VM-Instance-ID.bin -vsv C:\VM\VM-Instance-ID.vsv -dmp C:\dir\crashdump.dmp
•	Create a dump file from the VM name and snapshot: 
o	Example: 
	vm2dmp.exe -vm VMName -dmp C:\VM\crashdump.dmp
	vm2dmp.exe -vm VMName -snap vm VMName -snap-SP1 -dmp C:\VM\crashdump.dmp
•	Optionally, specify debugging symbols path using the -sym flag.
3.2.2	Forensic image
•	To take a snapshot of a virtual machine's memory in Hyper-V, you need to use the Checkpoint functionality, either via the Hyper-V Manager or PowerShell.
•	Prior to doing so, we recommend that you ensure the VM has checkpoints enabled and that they are configured as Standard checkpoints, rather than Production. As the UI indicates, we want to capture the current state of applications. Also take note of the Checkpoint File Location path, as that's the location to which the VMRS file will be written.
•	To create a checkpoint using the Hyper-V Manager, locate the appropriate VM, right-mouse click, and select Checkpoint.
•	To create a checkpoint using PowerShell, use the Checkpoint-VM command and pass in the Linux VM name as an argument:
o	PS > Checkpoint-VM -Name [VMName]
•	This will instruct Hyper-V to take the checkpoint. 
3.3	XEN/CITRIX XENSERVER
3.3.1	Using the xeCLI
•	Open a text console or SSH session to the XenServer host.
•	Obtain the domain ID of the VM: 
o	xe vm-param-get uuid=<vm_uuid> param-name=dom-id
•	Trigger an NMI to force a crash dump: 
o	xl trigger <dom_id> nmi
•	Verify the creation of the memory dump file in the configured location after the VM restarts.
3.3.2	Using XenCenter
•	Configure the guest OS to enable manual crash dumps (e.g., CrashOnCtrlScroll registry key for Windows).
•	Use the keyboard shortcut Ctrl+Scroll Lock+Scroll Lock in the VM console to trigger the crash dump.
•	Ensure that XenCenter console options do not interfere with keyboard shortcuts.
3.3.3	OVA Extraction and Analysis
3.3.3.1	What is OVA?
•	An Open Virtualization Archive (OVA) is a compressed file containing the virtual machine’s disk and metadata a provision provided by the Citrix XenServer.
3.3.3.2	Procedure for OVA Extraction:
•	Open the OVA file using a zip extraction utility.
•	Extract contents, including VMDK, MF, and OVF files.
•	Convert the VMDK file to other formats (e.g., VHD) for compatibility with other virtualization platforms.
3.3.3.3	Precautions
•	The virtual machine must remain offline during the procedure.
•	Ensure all artifacts are hash-verified for integrity.
3.4	RHEV
3.4.1	Memory Dumps
•	Verify Virtual Machine Configuration
o	Identify the virtual machine you need to investigate.
o	Check its allocated memory using the following command: $ oc get vm <vm_name> -o yaml | grep memory
o	Example output: memory: 4Gi
o	Note: The allocated memory size impacts the time required to create and download the dump.
•	Create a Memory Dump
o	Use the virtctl memory-dump command to generate the memory dump:
	$ virtctl memory-dump get <vm_name> \
> --create-claim --claim-name=<vm_name>-mem \
>--output=<output_file_name>.tar.gz
	Replace <vm_name> with the virtual machine's name and <output_file_name> with the desired output file name.
o	Monitor the progress. Example output:
PVC <namespace>/<vm_name>-mem created
Successfully submitted memory dump request of VM <vm_name>
Waiting for memorydump to complete, current phase: Associating...
Waiting for memorydump to complete, current phase: InProgress...
Memory dump completed successfully
Downloading file: <file_size> [==================>] <download_speed>
Download finished successfully
o	Verify the memory dump file integrity using hashing algorithms (e.g., MD5, SHA256):
	$ sha256sum <output_file_name>.tar.gz
3.4.2	Forensic Images
•	Identify Virtual Disk
o	Locate the virtual disk associated with the VM. Use the RHEV Manager interface or CLI commands to identify the disk path or logical volume. 
	$ lvs | grep <vm_name>
•	Create a Forensic Image
o	Use imaging tools to create a bit-by-bit copy of the virtual disk:
	For dd: $ dd if=/dev/<disk_path> of=<output_file>.dd bs=4M status=progress
	For FTK Imager: 
•	Select the disk as the source.
•	Choose the desired output format (e.g., .E01, .dd).
o	Verify the forensic image integrity:
	$ sha256sum <output_file>.dd
o	Store the forensic image on a write-protected medium for further analysis.
