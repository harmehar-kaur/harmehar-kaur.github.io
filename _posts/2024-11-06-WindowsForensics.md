---
title: Windows Forensics Artefact: Registry Hives
date: 2024-11-06
categories: [Windows Forensics Artefacts, DFIR]
tags: [Forensics, Registry,SAM, Security, System, Software]
author: Harmehar Kaur
image:
  path: /assets/malware.png
  alt: Cyber
---

## Windows Forensics Artefact: Registry Hives

The Windows Registry is a hierarchical database that stores system configuration information in the form of key-value pairs. It can be accessed via `regedit.exe` or by navigating to the path:  
`C:\Windows\System32\Config`

### Main Registry Hives

There are five main registry hives in Windows:

- **DEFAULT**
- **SAM** – Stores information about user accounts, login details, group information  
- **SECURITY**
- **SOFTWARE**
- **SYSTEM**

In addition, user-specific registry hives include:

- **NTUSER.DAT**  
- **USRCLASS.DAT**  
These plug in as `HKEY_CURRENT_USER` and are located in the user’s directory.

### Root Registry Keys

There are 5 root keys:

- `HKEY_CURRENT_USER` – Subkey of `HKEY_USERS`, contains user-specific settings
- `HKEY_USERS` – Stores all actively loaded user profiles
- `HKEY_LOCAL_MACHINE` – Configuration specific to the machine
- `HKEY_CLASSES_ROOT` – Subkey of `HKEY_LOCAL_MACHINE`, stores file association data
- `HKEY_CURRENT_CONFIG` – Contains hardware profile info of the local machine

---

## Registry Transaction Logs and Backups

- **Transaction Logs:**  
  Stored as `.log` files in the same directory as the hives. They contain recent changes not yet committed to the hive.

- **Backups:**  
  Hives are backed up every 10 days to:  
  `C:\Windows\System32\Config\RegBack`

### Additional Backup Locations

- Windows XP: `C:\Windows\Repair`
- Windows Vista and later: `C:\Windows\System32\config\RegBack`

---

## Registry Data Types

| Name                          | Type Description                                                |
|-------------------------------|------------------------------------------------------------------|
| `REG_BINARY`                 | Raw binary data                                                 |
| `REG_DWORD`                  | 32-bit integer                                                  |
| `REG_QWORD`                  | 64-bit integer                                                  |
| `REG_SZ`                     | Fixed-length text string                                        |
| `REG_EXPAND_SZ`             | Variable-length data string                                     |
| `REG_MULTI_SZ`              | Multiple strings separated by delimiter                         |
| `REG_NONE`                   | No data type                                                    |
| `REG_LINK`                   | Unicode string naming a symbolic link                          |
| `REG_RESOURCE_LIST`          | Nested arrays for resource lists                                |
| `REG_RESOURCE_LIST_REQUIREMENTS_LIST` | Lists possible hardware resources for drivers     |
| `REG_FULL_RESOURCE_DESCRIPTOR` | Used by physical hardware devices                             |

> Timestamps in the registry reflect the **Last Write Time** and are stored in **UTC**.

---

## Key Areas of Interest in Registry Hives

### 1. User & System Info – SAM Hive

Path: `HKEY_LOCAL_MACHINE\SAM\Domains\Account\Users`  
Information includes:

- Username
- SID
- Created time
- Last login
- Number of logins
- Password policy
- Group information

### 2. System Settings – SYSTEM Hive

Path: `HKLM\SYSTEM`  
Used during boot to load drivers and services.

- `ControlSet001`, `ControlSet002`, etc. – Backup control sets
- `CurrentControlSet` – Active config set used during system run

**Computer Name:**

- Local: `HKLM\SYSTEM\<ControlSet>\Control\ComputerName\ComputerName`
- Network: `HKLM\SYSTEM\<ControlSet>\Services\Tcpip\Parameters`

**Windows Version & Install Date:**  
`HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion`

**Network Interfaces:**  
`HKLM\SYSTEM\<ControlSet>\Services\Tcpip\Parameters\Interfaces`

---

## Program Execution – Application Compatibility (ShimCache)

### Windows XP:
- Path: `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatibility`

### Windows Vista+:
- Path: `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache`

- Tracks executable files: filename, location, size, last execution, modification time, flags
- Updated at shutdown

### `RecentFileCache.bcf` – Windows 7:
- Temporary cache at: `C:\Windows\AppCompat\Programs\RecentFileCache.bcf`
- Processed by ProgramDataUpdater task

### `Amcache.hve` – Windows 8+:
- Format: REGF
- Location: `C:\Windows\AppCompat\Programs\`
- Provides extensive info about executed programs

More info: [Amcache Analysis by Swift Forensics](https://www.swiftforensics.com/2013/12/amcachehve-in-windows-8-goldmine-for.html)

---

## User Activity – NTUSER.DAT

### Trusted Documents:
- Tracks trusted Office files:
  - Word:  
    `Software\Microsoft\Office\<version>\Word\Security\Trusted Documents\TrustRecords`
  - Excel / PowerPoint:  
    Similar paths for other Office apps

### Internet Link Tracking:
- Path: `NTUSER.DAT\Software\Microsoft\Office\<version>\Common\Internet\UseRWHlinkNavigation`

### RecentDocs:
- Path: `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs`

### Run Commands:
- Path: `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU`

### Typed URLs & Paths:
- URLs: `NTUSER.DAT\Software\Microsoft\Internet Explorer\TypedURLs`
- Paths: `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths`

### OpenSavePidlMRU:
- Path: `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePidlMRU`

### LastVisitedPidlMRU:
- Path: `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidlMRU`

### UserAssist:
- Tracks user activity using ROT-13 encoding
- Path: `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\`

### MuiCache:
- Path:  
  `HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\MuiCache`
- Records names of executed executables

---

## Autorun Keys & Malware Persistence

### Autorun Registry Keys:

- Pre-login (all users):  
  `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run`  
  `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce`

- Post-login (current user):  
  `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`  
  `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce`

### Winlogon Feature:
- Manages logon/logoff processes  
- Keys of interest:
  - `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\Shell`
  - `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\UserInit`  
  - Malware may add to `UserInit` value to ensure persistence

---

## User Registry Hives

### `NTUSER.DAT`:
- Stores individual user preferences, file activity, etc.  
- Location: `C:\Users\<Username>\NTUSER.DAT`

### `USRCLASS.DAT`:
- Stores user interface settings and file associations  
- Location: `C:\Users\<Username>\AppData\Local\Microsoft\Windows\UsrClass.dat`
