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
4	TAKING MEMORY DUMP AND FORENSIC IMAGE OF TYPE 2 HYPERVISOR 
4.1	VMWARE WORKSTATION / FUSION 
4.1.1	Memory Dumps 
•	Identify the installation directory of VMware Workstation or Fusion based on your operating system. 
o	Windows (32-bit): C:\Program Files\VMware\VMware Workstation\
o	Windows (64-bit): C:\Program Files (x86)\VMware\VMware Workstation\
o	Linux: /usr/bin/
o	Mac OS: /Library/Application Support/VMware Fusion/
•	Ensure the vmss2core tool is available in the directory. If not, download it from a trusted source such as vmss2core on Archive.org.
•	Use the following commands to create a memory dump: 
o	For Windows Guest OS: vmss2core.exe -W virtual_machine_name.vmss virtual_machine_name.vmem
o	For Windows 8/8.1, Server 2012/2016/2019 Guest OS: vmss2core.exe -W8 virtual_machine_name.vmss virtual_machine_name.vmem
o	For Linux Guest OS:./vmss2core-Linux64 -N virtual_machine_name.vmss
4.1.2	Creating forensic image 
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
4.2	ORACLE VIRTUAL BOX 
4.2.1	Memory Dump
•	Dumping VM Memory to an ELF File
o	Use the following command to generate a core dump of the running VM:
	$ VBoxManage debugvm <VM_Name> dumpvmcore --filename=<Output_File_Name>.elf
	Replace <VM_Name> with the name of the running VM and <Output_File_Name> with your desired file name.
o	Example: $ VBoxManage debugvm Win7 dumpvmcore --filename=Win7.elf
•	Identifying the Memory Section in the ELF File
o	To locate the memory section in the ELF file, run:
	$ objdump -h <Output_File_Name>.elf | egrep -w (Idx|load1)
•	Extracting the Memory Dump
o	Use the size and offset values to extract the memory dump:
o	$ size=0x<SIZE_FROM_OBJDUMP>
o	$ off=0x<OFFSET_FROM_OBJDUMP>
o	$ head -c $(($size+$off)) <Output_File_Name>.elf | tail -c +$(($off+1)) > <Output_File_Name>.raw
•	Analyzing the Memory Dump with Volatility
o	Run the following command to analyze the memory image:
	$ python vol.py -f <Memory_File>.raw imageinfo
	Example:
•	$ python vol.py -f Win7.raw imageinfo
•	This command outputs suggested profiles and other useful details for further analysis.
 
