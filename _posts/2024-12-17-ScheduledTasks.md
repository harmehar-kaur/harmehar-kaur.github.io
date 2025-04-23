---
title: How Scheduled Tasks Work on Windows
date: 17 December 2024
categories: [DFIR]
tags: [Scheduled Tasks, Windows, Persistence, Cybersecurity, Forensics]
author: Harmehar Kaur
image:
  path: /assets/forensics.jpg
  alt: Scheduled Tasks in Windows
---

## How Scheduled Tasks Work on Windows

Task Scheduler is a handy feature in Windows that allows users or applications to automate the execution of programs based on certain trigger events. Users can interact with tasks through the Task Scheduler GUI (`taskschd.msc`), command-line tools like `schtasks.exe` and `at.exe`, or PowerShell’s Scheduled Tasks cmdlets. Additionally, it can be accessed programmatically via Windows APIs. Microsoft offers detailed examples of working with Task Scheduler, which you can check out for more insights.

### Two Main Components of Task Scheduling

There are two primary components that form the foundation of the Task Scheduler infrastructure:

1. **Task Definitions**
2. **Task Scheduling**

#### Task Definitions
Task definitions outline the actions to be performed by the Task Scheduler. These are the critical aspects that we’re interested in when investigating intrusion cases:

- **Triggers**: Triggers determine when a task runs. These can be time-based (e.g., run daily at 4 PM) or event-based (e.g., run on system boot). A task can have multiple triggers.
- **Actions**: Actions typically point to an executable or script with optional arguments. In some cases, it might involve a ComHandler GUID, which you’ll need to look up in the Windows registry.
- **Principals**: This defines the user under whose context the task will run, such as NT Authority\SYSTEM or a user group.

#### Task Scheduling
Task scheduling is where the system actually carries out the tasks defined. This job is performed by the Windows service “Schedule.” Once this service starts, it loads all task definitions into memory and keeps track of the triggers, actions, and principles. If a task is newly created, modified, or deleted, the Task Scheduler updates accordingly.

### How Threat Actors Abuse Scheduled Tasks

Scheduled tasks are frequently used by threat actors for persistence. They can run automatically based on a predefined trigger (such as when a user logs in or the system boots up). Since many legitimate tasks exist on Windows, a malicious task can easily blend in, making it harder to detect. Furthermore, threat actors might modify an existing task by adding or changing actions.

Beyond persistence, scheduled tasks can be abused to execute commands remotely. A popular tool for this purpose is Impacket's `atexec.py` script. Scheduled tasks also provide a convenient method for privilege escalation to SYSTEM if the right permissions are in place. You can read more about this in MITRE ATT&CK technique T1053-005.

### Scheduled Task Artifacts

There are several sources of evidence to investigate when dealing with scheduled tasks. These can be divided into three primary categories:

- **Tasks Defined on Disk**
- **Tasks Defined in Memory**
- **Task History from Event Logs**

#### Tasks Defined On Disk
A host’s current task definitions are stored in multiple locations:

- `C:\windows\tasks`
- `C:\windows\system32\tasks`
- `C:\windows\system32\config\SOFTWARE`
- `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tasks`
- `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tree`
- `%localappdata%\Microsoft\Windows\PowerShell\ScheduledJobs`

##### Breakdown by Windows Version:
- **Windows XP**: Task definitions are found in `C:\windows\tasks` as binary `.job` files, which follow Task Scheduler 1.0 specifications.
- **Windows Vista & 7**: Task Scheduler 2.0 stores tasks in `C:\windows\system32\tasks`. Tasks may also be found in `C:\windows\tasks` if created using Task Scheduler 1.0 (e.g., via `at.exe`).
- **Windows 8 and newer**: Starting with Windows 8, task definitions are stored primarily in the registry, although XML files still populate `C:\windows\System32\Tasks`. Deleting the XML file on disk will not remove the task if the registry entry exists. The two primary registry keys involved are:
  - `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tree`
  - `HKLM\Software\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tasks`

#### PowerShell Scheduled Jobs
PowerShell scheduled jobs combine PowerShell jobs and scheduled tasks. These are stored in the following locations:
- `C:\Windows\System32\Tasks\Microsoft\Windows\PowerShell\ScheduledJobs`
- `%localappdata%\Microsoft\Windows\PowerShell\ScheduledJobs`

A PowerShell scheduled job will execute only when triggered by a corresponding scheduled task.

#### Tasks Defined In Memory
Scheduled tasks that are active in memory are stored within the process memory of the `svchost` process hosting the Schedule service. However, most tools do not provide the ability to parse task data from `svchost` memory. Tools like TaskHunter.ps1 or MemProcFS can be used for this purpose.

#### Task History from Event Logs
Event logs provide insight into the historical artifacts of tasks, including when a task was created, updated, or deleted. Specifically, there are three important event IDs for task artifacts:
- **4698**: Task created
- **4699**: Task deleted
- **4702**: Task updated

Additionally, task execution events can be logged in the Microsoft-Windows-TaskScheduler/Operational log, such as:
- **Event 100**: Task started
- **Event 200**: Action started
