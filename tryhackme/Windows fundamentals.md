
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

• Some examples in CMD 

| Command                             | Description |
|-------------------------------------|-------------|
| `hostname`                          | Shows the **name of the computer** |
| `whoami`                            | Displays the **logged-in user's name** |
| `ipconfig`                          | Shows a **summary of current IP configuration** for each network adapter |
| `netstat`                           | Displays **network connections, routing tables, port activity** |
|                                     | ▸ `-a` → All connections (incoming + listening), but no program info |
|                                     | ▸ `-b` → Binaries (shows the program/executable using each connection) |
|                                     | ▸ `-e` → Ethernet statistics (bytes sent/received, errors) |
|                                     | ▸ `-an` → All numeric (IP addresses and ports only, no DNS) |
| `net`                               | Manage **network resources and configuration** |
|                                     | ▸ `user` → Manage local user accounts |
|                                     | ▸ `localgroup` → Manage local groups |
|                                     | ▸ `session` → View active sessions (when file sharing is enabled) |
|                                     | ▸ `start` / `stop` → Start or stop Windows services |
| `echo %windir%`                     | Displays the value of the `%windir%` environment variable (Windows folder) |
| `start %windir%\notepad.exe`        | Launches Notepad from the Windows directory |
| `echo Hello > file.txt`             | Writes the text "Hello" to a visible file |
| `echo Secret > file.txt:hidden`     | Writes hidden content to an alternate data stream |
| `more < file.txt:hidden`            | Reads hidden content from an alternate data stream |



•adding /? after a command retrieves help manual for that command

---

# ⌨️ **Keyboard useful combinations**

• lusrmgr.msc      ➝ Opens the Local Users and Groups Manager (available on Pro & higher editions)

• ctrl+shift+esc      ➝ opens task manager

• win + r + taskmgr           ➝ opens task manager

• win + r +UserAccountControlSettings       ➝ opens UAC

• win + compmgmt      ➝ opens computer managment ( contains UAC for example,task scheduler , Local Users and Groups Manager etc...)

• win + perfmon      ➝ opens performance monitor

• win + msinfo32      ➝opens system information

• win + resmon      ➝opens resource monitor "includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict " - Microsoft

• win + cmd      ➝opend command prompt
