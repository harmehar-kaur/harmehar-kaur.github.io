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
6	MEMORY DUMPING: LIME
•	LiME is a popular open-source tool used to create a memory image of a running Linux system. A Loadable Kernel Module (LKM) which allows for volatile memory acquisition from Linux and Linux-based devices, such as Android. This makes LiME unique as it is the first tool that allows for full memory captures on Android devices. It also minimizes its interaction between user and kernel space processes during acquisition, which allows it to produce memory captures that are more forensically sound than those of other tools designed for Linux memory acquisition.
6.1	COLLECTING MEMORY DUMPS: 
•	Prerequisites:
o	Ensure the following are installed on your system:
	Git: For cloning the LiME repository.
	Build-essential: For compiling the LiME module.
	Linux Kernel Headers: Needed for building kernel modules.
o	Install the required packages:
	sudo apt update
	sudo apt install git build-essential linux-headers-$(uname -r)
•	Clone the LiME Repository
o	git clone https://github.com/504ensicsLabs/LiME.git
o	Navigate to the cloned directory:
	cd LiME
•	Compile the LiME Module
o	Go to the `src` directory within the LiME repository:
	cd src
o	Compile the module using `make`:
	make
o	Ensure the `lime.ko` file is generated in the `src` directory.
•	Load the LiME Module
o	Use the `insmod` command to load the LiME module into the Linux kernel. Specify the path where you want to save the memory dump and the desired format (e.g., `raw` or `lime`).
o	Save Locally:
	For example, save a memory dump in `raw` format to `/path/to/dump.mem`:
	Check the `/path/to` directory for a `.mem` file.
o	Save Over a Network:
	To send the memory dump over a network, specify the IP address of the receiving machine and the desired port:
	sudo insmod lime.ko path=tcp:192.168.1.2:4444 format=lime
	Replace `192.168.1.2` with the IP address of the target machine. Replace `4444` with the port number.
•	Verify the Memory Dump**
o	If saved locally, navigate to the specified directory and check for the `.mem` file:
	ls -lh /path/to/
o	If sent over a network, ensure the receiving machine has a listener ready to capture the memory dump (e.g., using `nc` or `netcat`):
	nc -l -p 4444 > memory_dump.lime
•	Unload the LiME Module (Optional)
o	After collecting the memory dump, you can remove the LiME module from the kernel:
	sudo rmmod lime
