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
4	COLLECTING TRIAGE DATA from linux systems: UAC AND VELOCIRAPTOR  
Some forensically sound tools that could be used to collect triage data on linux systems are as follows: 
4.1	UAC
4.1.1	What is UAC?
•	Unix-like artifact collector used to collect triage data from a Unix-like system. 
•	UAC is a free tool that gathers important forensic data from Unix-like systems, including Linux. It consists of a single shell script, making it easy to use on various Unix platforms, but it relies on several configuration files. 
•	To use UAC, follow these steps: 
o	Set up any necessary network services for storing the output, like SFTP or S3.
o	Transfer the TAR file containing the script and configuration files to the Linux system.
o	Run the collector as the root user, specifying what data to collect and where to save the results(save the results to an external device).
4.1.2	What UAC does? 
•	Collects items such as browser history, /var/log contents which contain many Linux logs, tmp file, Linux body file, live system information.
•	Features of the tool as described by the documentation:
o	Run everywhere with no dependencies (no installation required).
o	Customizable and extensible collections and artifacts.
o	Respect the order of volatility during artifact collection.
o	Collect information from processes running without a binary on disk.
o	Hash running processes and executable files.
o	Extract information from files and directories to create a bodyfile (including enhanced file attributes for ext4).
o	Collect user and system configuration files and logs.
o	Collect artifacts from applications.
o	Acquire volatile memory from Linux systems using different methods and tools.
4.1.3	How to run and collected triage data using UAC 
•	The installation of UAC downloads a tar.gz file which when decompressed contains the following folders or files: 
o	Artifacts - Contains a listing of what to collect. This can be customized 
o	Bin - You can place additional binaries here that you may want to use for your collections 
o	Tools - Various *nix scripts the collector may use as part of its normalization 
o	Profiles - Contains the profiles of the collectors. These essentially define what "artifacts" will be collected. By default, this comes with three profiles, but you can make your own
o	uac - The shell script file 
4.1.3.1	Step-by-step process
•	Install the latest release from the GitHub: https://github.com/tclahr/uac/releases
•	Decompress the archive using the following command: 
o	tar -xf uac_file_downloaded_name.tar.gz
•	to run the script for collection using command: 
o	sudo ./uac -p full /path/to/external/drive
