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
3	FTK IMAGER for imaging windows systems
•	It is an open-source data preview and imaging tool which allows the collection of electronically stored information in a forensically sound manner. 
•	It is advised to avoid having an active connection on the device whose image is to be created by the imager. 
•	The imager could be used in 2 ways to:
o	By locally installing it into a device 
o	Or by storing it on a removable device which could be connected to the device keeping in consideration the usage of write blocker and then used to create an image of the device or system of interest or under examination.  
•	It could be used for 
o	Evidence viewing 
o	Memory dumping or making a forensic image
3.1	USER INTERFACE OF IMAGER:
•	The imager when launched consists of several panes which appears as follows: 
•	The key point to remember in order to traverse the UI of the FTK imager:
o	The menu pane gives access to all features of FTK imager and consists of file menu, view menu, mode menu and help menu. 
o	The mode menu in the menu pane allows 3 preview modes:
o	Automatic: chooses the best view like embedded windows explorer for webpages
o	Text: preview as ASCII or Unicode character, is often used to view text/binary files. 
o	Hex: views every byte of data as hexadecimal code. 
o	Evidence opened could be viewed as a tree structure in the evidence tree pane or as file list under the file list pane which only shows the contents of the directory currently selected in the evidence tree. 
3.2	CREATING FORENSIC IMAGE: 
•	The best and safest way for creating a forensic image is by making a physical copy of the hard drive. To achieve which the drive is removed from the computer and is connected with another computer using a write blocker. And then use a imaging software to create a physical image of the drive. 
•	Encryption is employed: the physical image serves no useful purpose if the drive encrypts the original content since it would lead to the image being encrypted as well. In this case the image taken is logical image. 
•	Steps to create an image with FTK imager:
o	Open FTK Imager: Launch the software and click the "Add New Evidence" button in the upper left corner.
o	Select Source:
	In the Source Selection Menu, choose one of the following options: 
•	Physical Drive
•	Logical Drive
•	Preexisting Image File
•	Contents of a Specific Folder
o	Import Physical or Logical Device:
	If importing a Physical Device, select the desired hard drive from the displayed list.
	If importing a Logical Device, select the desired partition.
	If importing an Image File or Folder, browse for the appropriate image or folder to import.
o	Load Evidence:
	After selecting the device, click "Finish" to load the evidence into FTK Imager.
	Verify the loaded evidence by browsing it in the Evidence Tree on the left-hand side.
o	Export as Disk Image:
	Right-click the device in the Evidence Tree and select "Export Disk Image".
	This will start the Image Creation Wizard.
o	Configure Image Settings:
	Click "Add" in the wizard.
	Ensure the "Verify images after they are created" option is checked (uses hashing to ensure accuracy).
o	Select File Type:
	Choose the output image file type from options such as: 
•	DD: Pure bitstream format.
•	SMART: Commercial format (rarely used).
•	AFF: Supports encryption and compression.
•	E01: Common proprietary format with compression support. 
o	Add Case Metadata: Include case data (metadata) in the image for identification purposes.
o	Set File Parameters:
	Assign a name to the image.
	Configure parameters for compression and fragmentation: 
•	Compression: Slows down creation but saves storage space.
•	Fragmentation: Determines the size of image file segments.
o	Start Image Creation:
	Click "Start" in the Create Image menu.
	The process will begin, creating the image as per the specified parameters.
3.3	COLLECTING MEMORY DUMPS
•	Since memory could hold information like encryption keys or content in decrypted form or some more information that may interest a forensic examiner dumping the memory could be a counted as a important way to collect data from the system of interest or under examination. 
•	Memory dumping is only possible in case of live examination. 
•	In case of FTK imager it is easy to capture a memory dump for a device: simply select “Capture memory” then the destination path and file name and press “OK”. 
•	Now memory dumps usually are stored in big files therefore it is important to make sure that the destination file system allows storage of big files. 
3.4	COLLECTING REGISTRY HIVES 
•	FTK imager could also be used to collect registry hives. The steps followed for which are as follows: 
o	Click on the “obtain protected file” button 
o	A menu appears which allows to select whether all available registry files are needed or only those for password recovery along with which one has to put in the destination path and press “OK”. 
