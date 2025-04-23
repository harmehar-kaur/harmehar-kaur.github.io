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
5	FORENSIC IMAGING 
5.1	USING DD COMMAND
-	Steps to be followed in order to create a forensic image of linux system using dd command is as follows:
o	List all the devices to identify disk device for imaging:  lsblk

 
o	Listing the partition table for disk devices: fdisk -l 

o	dd if= /dev/sdb/ of= /path/to/external/device/imag.img status=progress 

o	md5sum /destination/imag.img > imagemd5.md5


o	for hashing while imaging we can use the command dcfldd or can separately hash it and store in a text file.
	dcfldd if =/dev/sdb/ of= destination/image.img hash=hash_value hashwindow=1M hashlog= destination-folder/file.hash status=[on|off]
	dc3dd if=/var/log/messages of=/tmp/dc3dd hash=sha512
