# 📡 **Authentication Protocols**

• `netNTLM ` - an old Windows authentication method.Used when my computer needs to prove who I am to a server or another computer.How it works :
1. I type my username & password.
2. my computer turns the password into a hash (a scrambled code).
3. It sends the hash to the server instead of the plain password.
4. Server checks the hash — if it matches, I am allowed in.

---

• `Kerberos ` - the newer, safer Windows authentication method (used in Active Directory).How it works :
1. I log in with my username & password.
2. The Domain Controller (DC) gives me a Ticket Granting Ticket (TGT) — this is like a VIP pass for requesting access to other servers.
3. Whenever I want to access a specific server or resource, my computer uses the TGT to request a service ticket for that server.
4. I present the service ticket to the server
5. The server checks the ticket → if it’s valid, it lets me in.













---

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
| `ipconfig`  | Shows a **summary of current IP configuration**             | `ipconfig`  ,`ipconfig/all`                                    |
| `netstat`                           | Displays **network connections(protocols,local addresses etc), routing tables, port activity** |       |
|                                     | ▸ `-a` → All connections (incoming + listening), but no program info |       |
|                                     | ▸ `-b` → Binaries (shows the program/executable using each connection) |       |
|                                     | ▸ `-e` → Ethernet statistics (bytes sent/received, errors) |       |
|                                     | ▸ `-an` → All numeric (IP addresses and ports only, no DNS) |       |
|                                     | ▸ `-n` → Shows all connections using numerical IP addresses and port numbers instead of trying to resolve hostnames. |            |
|                                     | ▸ `-o` → Displays the Process ID (PID) of the process using each connection. |            |
|                                     | ▸ `-abon` →complete view of every connection and listening port, who owns it, and which process is using it. |            |
| `net`                               | Manage **network resources and configuration** |       |
|                                     | ▸ `user` → Manage local user accounts |       |
|                                     | ▸ `localgroup` → Manage local groups |       |
|                                     | ▸ `session` → View active sessions (when file sharing is enabled) |       |
|                                     | ▸ `start` / `stop` → Start or stop Windows services |       |
| `echo`      | Displays messages or environment variables                   | `echo %windir%` `echo Hello > file.txt` `echo Secret > file.txt:hidden` |
| `start`     | Launches a program or opens a file/folder                    | `start notepad` `start %windir%\notepad.exe` |
| `more`      | Displays output one screen at a time                         | `more < file.txt` `more < file.txt:hidden`  |
| `systeminfo `      | display detailed information about your computer’s system configuration, hardware, and software environment | `systeminfo `  |
| `ver`      | Determine the operating system (OS) version| `ver`  |
| `set`      | Typing set alone lists all environment variables currently defined in your session.I can define a new variable or change an existing one:| `set` ,`set MYVAR=HelloWorld` |
| `driverquery `      | display a list of all installed device drivers on your system, along with details about each driver | `driverquery` , `driverquery /v ` (Verbose mode. Shows more details about each driver, including description, version, and start type.) |
| `help`   ,` help [command] `    | Displays information on the command that was types,if only help was typed,outputs all commands and their usages              | ` help cls`  |
| `cls`      | Clears cmd screen | `cls` |
| `ping `      |test connectivity between your computer and another device (like a website, server, or another computer) on a network. It also shows how long it takes for data to travel back and forth, called the “round-trip time.”.By default, ping sends 4 requests | `ping google.com`, `ping 8.8.8.8` |
| `tracert`      | shows the path that network packets take from my computer to a destination, like a website or IP address. It tells me each “hop” along the way and how long it takes to reach that point. | `tracert google.com` , `tracert 8.8.8.8` |
| `nslookup`      | used to look up DNS information | `nslookup google.com` |
| `nslookup`      | used to look up DNS information | `nslookup google.com` |
| `cd`      |used to navigate between folders in your file system | `cd C:\Users\YourName\Downloads` , `cd Documents` , `cd ..` ➝ go up one folder level|
| `dir`      |lists the contents of the current directory (files and folders) | `die /b` ➝ Shows files in a simple list (like ls) , `dir /a ` ➝Shows all files (including hidden ones)| 
| `tree`      | used to display a graphical (text-based) view of the folder structure | `tree` |
| `mkdir <foldername>`      | creates a folder | `mkdir Pictures_from_Spain` |
| `rmdir <foldername>`      |  removes folders.If the folder is not empty, I must use the /s flag: | `rmdir /s Hwk1` |
| `type`      | display the contents of a text file directly in the terminal | `type file1.txt` , `type nul > file1.txt` ➝creates an empty file |
| `more`      | if the expected output is too long we add more after command and press on spacebar if we need to moce by one page or enter if we want to move by 1 line | `driverquery more`  |
| `copy`      |  copies contents from one file to another | `copy test1.txt test2.txt` ,`copy *.md C:\Markdown`|
| `move`      |  Renames or relocates one file to another | `move test1.txt test2.txt` |
| `tasklist`      | displays a list of all currently running processes on my computer. Text-based version of Task Manager. | `tasklist` ,  ` tasklist /FI "imagename eq sshd.exe" ` /FI → Filter the results, "imagename eq sshd.exe" → Only show processes where the Image Name equals sshd.exe |
| `taskkill /PID target_pid`      |  terminates/kills the designated task | `taskkill /PID 4567` |
| `chkdsk`      |  scans a drive (like C:) for errors and can fix certain problems with the file system or bad sectors on the disk. | `chkdsk ` → lists the status of the current drive (usually C:) without making changes , `chkdsk /f` →Fixes errors on the disk , `chkdsk /r` →Locates bad sectors and recovers readable info |
| `sfc /scannow`      | scans all protected system files on my Windows installation.If it finds corrupted or missing system files, it attempts to repair or replace them automatically. | `sfc /scannow` |
| `shutdown /s`| shuts down a system | `shutdown /s` |
| `shutdown /r`| restarts a system | `shutdown /r` |
| `shutdown /l`| Log off the current user | `shutdown /l` |
| `powershell`| Launches powershell, as we will see PS in the beginning of the next command line | `powershell` |


📝 Note:

•adding /? after a command retrieves help manual for that command

---

• Some examples in Powershell

| Command     | Description                                                  | Examples                                      |
|-------------|--------------------------------------------------------------|-----------------------------------------------|
| `hostname`  | Shows the **name of the computer**                           | `hostname`                                    |
| `Get-Command`  | find all available commands on your system — including cmdlets, functions, aliases, scripts, and executable programs. | `Get-Command` ,` Get-Command -CommandType "Function"`, ` Get-Command -Name "Remove*" ` |
| `Get-Help`  | displays help information about commands, concepts, and features in PowerShell.| `Get-Help Get-Date`  |
| `Get-Alias`  |shows me the aliases currently defined in my PowerShell session,for example ls → alias for Get-ChildItem | `Get-Alias`  |
| `Set-Location -Path`  |Navigates to the specified directory or location (similar to cd in Linux/Ubuntu) | `Set-Location -Path ".\Documents"`  |
| `New-Item`  |create a new item — such as a file, folder, registry key, etc. (similar to touch/mkdir in Linux/Ubuntu) | `New-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt" -ItemType "File"`  |
| `Get-ChildItem`  | lists the contents of a location — such as files and folders in a directory. (ls is Linux, dir in cmd)| ` Get-ChildItem -Path C:\Users`  |
| `Sort-Object` , `sort`  | used to sort PowerShell objects (like files, processes, numbers, text, etc.) based on one or more of their properties. | `  Sort-Object Length`  |
| `Where-Object` ,`where` ,`?`   |filtering cmdlet. It lets me select objects from a collection based on a condition I specify |   |
|                                     | ▸ `-eq` → equal |       |
|                                     | ▸ `-ne` → not equal |       |
|                                     | ▸ `-gt` → greater than |       |
|                                     | ▸ `-ge` → greater than or equal to |       |
|                                     | ▸ `-lt` → less than |       |
|                                     | ▸ `-le` → less than or equal to |       |
|                                     | ▸ `-like` → allows wildcards (*, ?) for pattern matching. |       |
| ` Select-String`   |searches for text patterns (like words, phrases, or regex patterns) inside files or command output, similar to how grep works in Linux. | `Select-String -Path "notes.txt" -Pattern "error"` , `Select-String -Path ".\captain-hat.txt" -Pattern "hat"`   |
| `Get-ComputerInfo `  |retrieves detailed information about my computer and operating system | `Get-ComputerInfo`  |
| `Get-LocalUser `  |lists all the local user accounts on my computer | `Get-LocalUser `  |
| `Get-NetIPAddress `  |shows all IP address configuration details on your computer — both IPv4 and IPv6 addresses for all network adapters. | `Get-NetIPAddress`  |
| `Get-Content `  |reads the contents of a file and displays them line by line —just like cat in Linux or type in  CMD. | `Get-Content file1.txt `  |
| `Get-Process `  |shows all the processes currently running on my computer | `Get-Process`  |
| `Get-Service `  |lists all Windows services that are registered with the Service Control Manager (SCM) — that’s the system that manages Windows services. | `Get-Service`  |
| `Get-NetTCPConnection`  |shows all active TCP network connections on my computer. | `Get-NetTCPConnection`  |
| `Get-NetUDPEndpoint`  |shows all active UDP network connections on my computer. | `Get-NetUDPEndpoint`  |
| `Get-FileHash`  |calculates a cryptographic hash value (checksum) for a file. | `Get-FileHash`  |
| `Invoke-Command`  |lets me execute PowerShell code locally or remotely, and get the results back in my current session. | `Invoke-Command -ScriptBlock { Get-Process }` , `Invoke-Command -ComputerName "Server01" -ScriptBlock { Get-Service }`  |





more useful examples:
1. `1, 5, 3, 2 | Sort-Object`
2. `Get-ChildItem | Sort-Object Length -Descending`
3. ` Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"  `
4. `Get-ChildItem | Where-Object -Property "Name" -like "ship*" `








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

