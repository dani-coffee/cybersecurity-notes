
# 🧠 **Additional notes**
•  In a Remote Desktop session, some of the display settings will be disabled

---

• `NTFS (New Technology File System) ` - the main file system that Windows uses to store and manage data on hard drives and SSDs.

| Feature               | What It Means                                     |
|-----------------------|---------------------------------------------------|
| **File permissions**  | You can control who can read/edit files (ex:  disc C  ➝ properties ➝ security ➝ group or usernames (and chose an option) ➝ permission for `my choice from previous step` (and chose what I want: full control,modify etc) |
| **Large file support**| Can handle big files (over 4 GB)                  |
| **Reliability**       | Can recover from errors better than older systems |
| **Encryption support**| Supports file encryption (with Pro editions)      |
| **Compression**       | Lets you save space by compressing files          |
| **Alternate Data Streams (ADS)** | Allows hidden data to be attached to files without affecting the main content|

#####  example for ADS: in my already existing txt file I add the code 
      echo This is hidden data > normal.txt:hidden   
      then when I want to read the hidden file I type:    more < normal.txt:hidden    ➝ If I open my notepad I won't see the hidden message
  
•NTFS and older versions :

| File System | Used In           | Max File Size | Notes                                            |
|-------------|-------------------|---------------|--------------------------------------------------|
| **NTFS**    | Windows (default) | Very large    | Most powerful, supports all features             |
| **FAT32**   | Older systems     | 4 GB max      | Works everywhere but limited                     |
| **HPFS**    | OS/2, early Windows NT | 2 GB–4 GB     | Older file system, replaced by NTFS, not used today      |

---

• `System32 ` - this folder holds the important files that are critical for the operating system

---

• `UAC` (  User Account Control) - When a task requires administrator-level permission (like installing software or changing system settings), UAC:
1. Pauses the operation
2. Asks for confirmation (or admin credentials if you're on a standard account)
3.  Displays a popup, usually dimming the screen, with options like: "Do you want to allow this app to make changes to your device?"

---

• ` Task Manager` -  a built-in Windows tool that lets you monitor and manage running processes, programs, and system performance.
1. View running apps and background processes
2. End (kill) unresponsive programs
3. Check CPU, memory, disk, and network usage
4. Manage startup programs
5. See user activity
6. Monitor GPU performance


---

• `BitLocker` is a full‑disk encryption feature built into certain editions of the Microsoft Windows operating system. 
 It is designed to protect data on a drive by encrypting the entire volume so that the data cannot be read without proper authentication or the correct encryption key.
 
---

• `Shadow copies` - point‑in‑time snapshots of a disk volume (or shared folder) that capture the state of files and folders at a specific moment in time. 
They allow me to restore previous versions of files or folders, or recover files that were deleted or overwritten, by going back to an earlier “snapshot” state. 
They aso allow fast recovery from malware/ransomware: If a system is hit with ransomware, having shadow copies can allow you to revert files/folders to pre‑infection states — assuming the snapshots weren’t deleted by the attacker. Many ransomware strains attempt to delete or disable shadow copies before encryption.

---

• `Active Directory (AD)` -  a directory service made by Microsoft that helps manage users, computers, and other devices on a Windows network.It manages user accounts (who can log in),manages computers on the network,controls permissions & access (who can do what),organizes everything in a hierarchical structure.it’s a service that runs on a special computer called a Domain Controller (DC).Active Directory lets me centralize control of users, computers, and services — everything that needs to authenticate or follow security rules can join the domain.Every domain-joined machine has its own identity in AD — a machine account (with $ in the end) and a 120-character random password that rotates automatically for security.
`Security Groups` are objects stored inside AD.A `Security Group` in Active Directory (AD) A Security Group is a collection of users, computers, or other groups
used to assign permissions to resources (like folders, printers, or apps)..Instead of giving permissions to each person or computer one by one,I give them to a group, and everyone inside automatically inherits them. For example Backup Operators is a built-in Security Group in Windows and Active Directory (Members of this group have special permissions that let them back up and restore files,even if they normally wouldn’t have access to those files).An `Organizational Unit (OU)` is like a folder inside Active Directory.It’s used to organize and manage AD objects — such as users, computers, and groups — in a logical way. `Group Policy`  is a feature of Active Directory (AD) that lets administrators control settings on computers and user accounts across the network — automatically. Instead of manually configuring each PC (like setting wallpaper, password rules, or software),I define those settings once in a Group Policy Object (GPO) and AD applies them for me.
 

---



• Some examples in CMD 



| Command     | Description                                                  | Examples                                      |
|-------------|--------------------------------------------------------------|-----------------------------------------------|
| `hostname`  | Shows the **name of the computer**                           | `hostname`                                    |
| `whoami`    | Displays the **logged-in user's name**                       | `whoami`                                      |
| `ipconfig`  | Shows a **summary of current IP configuration**             | `ipconfig`                                    |
| `netstat`                           | Displays **network connections, routing tables, port activity** |       |
|                                     | ▸ `-a` → All connections (incoming + listening), but no program info |       |
|                                     | ▸ `-b` → Binaries (shows the program/executable using each connection) |       |
|                                     | ▸ `-e` → Ethernet statistics (bytes sent/received, errors) |       |
|                                     | ▸ `-an` → All numeric (IP addresses and ports only, no DNS) |       |
| `net`                               | Manage **network resources and configuration** |       |
|                                     | ▸ `user` → Manage local user accounts |       |
|                                     | ▸ `localgroup` → Manage local groups |       |
|                                     | ▸ `session` → View active sessions (when file sharing is enabled) |       |
|                                     | ▸ `start` / `stop` → Start or stop Windows services |       |
| `echo`      | Displays messages or environment variables                   | `echo %windir%` `echo Hello > file.txt` `echo Secret > file.txt:hidden` |
| `start`     | Launches a program or opens a file/folder                    | `start notepad` `start %windir%\notepad.exe` |
| `more`      | Displays output one screen at a time                         | `more < file.txt` `more < file.txt:hidden`  |

📝 Note:

•adding /? after a command retrieves help manual for that command

---


# ⌨️ **Keyboard useful combinations**

• lusrmgr.msc      ➝ Opens the Local Users and Groups Manager (available on Pro & higher editions)

• ctrl+shift+esc      ➝ opens task manager

• win + r + taskmgr           ➝ opens task manager

• win + r +UserAccountControlSettings       ➝ opens UAC

• win +r + compmgmt      ➝ opens computer managment ( contains UAC for example,task scheduler , Local Users and Groups Manager etc...)

• win + r + perfmon      ➝ opens performance monitor

• win + r + msinfo32      ➝opens system information

• win + r + resmon      ➝opens resource monitor "includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict " - Microsoft

• win + r + cmd      ➝opens command prompt

•win+ r + regedt32      ➝ opens the Windows Registry which is a centralized, hierarchical database used by the Microsoft Windows operating system to store low-level settings and configurations for both the OS and installed applications.Because the registry is so central to system operation, editing it incorrectly can cause serious problems (system instability, inability to start Windows, etc).

•win+ r + wf.msc      ➝opens windows firewall
