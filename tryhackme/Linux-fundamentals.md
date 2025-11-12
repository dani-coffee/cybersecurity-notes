# 🖥️ **Linux commands**
• `ls` -lists all items in the current directory (basic info: file and directory names)
##### ✏️examples:
        -ls
        -ls ~/Documents (if there's Documents folder in desktop)

• `ll` - like ls with the flag -l but shows hidden files too.It lists all items in the current directory but in a long format(more details: file permissions,number of links,owner name, group name,file size,modification date/time,filename)        

• `cd` - change directory (I have to insert a path(folders!!!))
 ##### ✏️examples:
         -cd Desktop (if I'm at my home directory and i do ls, i see Documents,I can do cd Desktop to got to this directory)
         -cd ..    ➝ I go back 1 step in my currrent path
         -cd ~    ➝ I go back to the home directory no matter where I currently am
         -cd ~/Desktop    ➝ if I wanna go back to Desktop directory 

• `echo` - prints an output to the terminal (adds automatically a newline in the end of a line,unless i add the flag -n)
#####  ✏️examples:
        - echo Hello world!    ➝ prints Hello world!
        - echo file1.txt
        - echo hi! > file1.txt
        - echo hi! >> file1.txt 
		- echo $SHELL	➝prints which shell I'm using
		
        
• `touch`-creating a new file
#####  ✏️examples:
        -touch file1.txt
        
• `cp`-copying content from one file to another
#####  ✏️examples:
        -cp file1.txt file2.txt

• `scp`-copying content from one file to another **securely**,using ssh protocol.
#####  ✏️examples:
        -scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt	➝see that the destination (ubuntu@192.168.1.30) syntax is exactly the syntax used to connect to a machine remotely using ssh.

• `rm`  -removing files (and only if i add -R flag, can remove folders too)
#####  ✏️examples:
        -rm file1.txt file2.txt 
        🔸note:if I want to remove the directory I have to add the flag -R
        -rm -R directory1
 
• `whoami` - tells me my username on my machine

• `whois` -used to look up information about domain names or IP addresses — it tells you who owns them, when they were registered, and other details.
##### ✏️examples:
        -whois twitter.com

• `mv` - moves a source file or a folder to the destination
#####  ✏️examples:
	-mv file1.txt file2.txt

• `mkdir` - creates a folder
#####  ✏️examples:
        -mkdir folder1
        
• `cat` -prints the contents of the inserted file
#####   ✏️examples:
            -cat file1.txt
            -cat ~/Desktop/file1.txt    ➝ I don't have to use cd to enter to the directory containing the file I want to print,I can just insert the parh adter using cat
			- cat etc/shells	➝prints all the available shells on my linux OS

• `nano` - edit file in terminal (easiest way for now click ctrl+O to save,enter,then ctrl+X to exit)
#####   ✏️examples:
        -nano file1.txt
		nano first_script.sh
       
• `pwd` - shows full path to the current directory

• `df`-shows disk space

• `find` - instead of continuously using ls and cd, I use this command to find what I need in the current directory and its subdirectories
##### ✏️examples:
        -find -name "file2.txt"    ➝ finds path of file2.txt,from current directory
        🔸note: in fact it's equivalent to find . -name "file2.txt" , the dot means the current directory
        -find -name "file1*"    ➝ using a wildcard means that any suffix is acceptable-this matches any file that starts with 'file1'

• `grep` - instead of using cat which prints all of the contents in a file ,I use this command to print the specific data I need and i prints the relevant output lines
##### ✏️examples: 
        -grep "passwords" file1.txt
        -grep -i "word" file1.txt    ➝ this one means case insensitive search and will search for WoRd ,WORD etc...
        -grep -c "word" file1.txt     ➝ counts how many lines contain the word "word"
        -grep -E "^" file1.txt    ➝ equivalent to cat file1.txt,'^'means the start of every line,-E stands for extended regular expression which enables extended regex         syntax.(like OR operator,or grouping expressions)

 • `file` - determining the file type

• `su` - switching user ( for that I must know the username and the password unless I'm logged into my superuser(explanation in Additional notes))
	🔸note: it's better to use `su -l` ( short for `--login`) because we start a shell that is much more similar to the actual user logging into the system

• `wget` - allows to download files from the web via http
##### ✏️examples: 
        -wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt

• `python3 -m  http.server` - turns my computer into a web server allowing me to download files from the web.If I use this ,I will have to open another terminal to execute my commands or just use operator `&` .To close,'i click `Ctrl+C`
##### ✏️examples: 
	-wget http://10.10.225.38:8000/myfile	➝ the structure is: announcing the http protocol,writing he ip_address (full web URL),the port and then the file name I want to pull.
	-wget http://10.10.225.38:8000/myfile &

• `ps` - viewing processes,shows information such as the pid( process id,its order).

• `ps aux` - see the processes run by other users and those that don't run from a session (i.e. system processes).

• `less` - file pager ,it lets me view (but not edit) the contents of a text file
##### ✏️examples: 
	-less file1.txt
	-ps aux | less
	
• `top` - shows real-time statistics about the processes running on my system instead of a one-time view,refreshes every 10s.
	`htop` does the same but the output is colorful
	to stop I do `Ctrl+C`

• `kill` - kill a process
##### ✏️examples: 
	-kill sigterm 23424	➝ kill process+allow to do cleanup tasks
	-kill 4242	➝default sigterm flag is used
	-kill sigkill 23424	➝ kill process,no cleanup tasks
	--kill sigstop 23424	➝doesn't kill just suspends/stops a process

• `systemctl` - this command allows us to interact with the systemd process/daemon. the format of the command is : systemctl [option] [service].
[option] are: start(launch now),stop,enable(start at boot),disable(not to start at boot)
##### ✏️examples: 
	-systemctl start apache2	➝tell apache to start up

• `fg`  bring a previously backgrounded process back to the foreground

• `crontab -e` - allows to schedule a certain action or task to take place after the system has booted,flaf `-e` stands for editig .It requires 6 values
MIN	What minute to execute at,HOUR	What hour to execute at,DOM	What day of the month to execute at,MON	What month of the year to execute at,DOW What day of the week to execute at,CMD The actual command that will be executed. `*` stands for-every
##### ✏️examples: 
	-0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/	➝backup "cmnatic"'s  "Documents" every 12 hours

 • `chsh` - a command that lets you change your default login shell
##### ✏️examples: 
	chsh -s /usr/bin/zsh

 • `history` - list of all the commands I’ve previously run in my shell session 

• `telnet` - old network protocol and command-line tool used to connect to remote computers over TCP (like SSH does today).Unlike SSH, Telnet is not encrypted, which is why it's rarely used today for secure remote access.
##### ✏️examples: 
	telnet 10.10.34.40 7	➝echo server
	10.10.34.40 13	➝daytime server
	telnet 10.10.34.40 80  then I add GET / HTTP/1.1 and Host: telnet.thm	➝web server

• `md5sum` -utility used to generate and verify MD5 (Message-Digest Algorithm 5) checksums for files.It’s often used to verify file integrity — to make sure a file hasn’t been corrupted or tampered with during transfer or storage.
##### ✏️examples: 
	md5sum filename.txt




# 🚩 **Flags**

• `--help` if I write a command accepting flags, and I add '--help' ,it prints all of the possible flags that can go along with this command,is equivalent to 'man' ( man stands for manual),which opens manual version on my machine.
##### ✏️examples: 
        -ls --help
	-grep --help
	-man grep


• `-h` - human readable format
##### ✏️examples: 
	-ll -h	➝ adds the unit in the line containing total
	-df -g	➝adds units to sizes ,making it understandable for us

• `-a` - short for `--all`,shows all the entries ,the regular once as well as the ones starting with `.`
##### ✏️examples: 
	-ls -a



# ⚙️ **Operators**
•`&` - allows to execute background operations while being able to do another operation
##### ✏️examples:
        echo "Start"
        sleep 5 &
        echo "I can type this immediately"


• `&&` - like in any other programming language ,it means logical and 
#####  ✏️examples:
    -echo Hi && echo There    ➝ prints  Hi
                                        There
                                        

•`>` - redirects output to the indicated file
        🔸note:if the indicated file doesn't exist, a new file with this name is created,otherwise the contents of the indicated fle are overwritten with the current             output.
#####  ✏️examples:
        -echo hi! > file1.txt


• `>>` - similar to '>' but this one appends,meaning even if the indicated file exists, it just adds the output to the file's original output 

•`|` - takes the ouutput of the left command and passes into the right command
#####  ✏️examples:
        -ps aux | less



# 📁 **Common Directories**
• `/etc` -  stores configuration files that are used by my operating system.It contains for example the `sudoers` file(who can use sudo and what commands they can run),as well as `passwd`(list of users and basic info about them like the username,home folder) and `shadow` files ( stores encrypted password hashes , often in sha512)

• `/tmp` - similar to how the RAM works. Stores data until the computer is restarted.

• `/root` -  the home directory of the `root` user, who is the superuser on a Linux system. The root user has full administrative privileges. This directory is different from `/home`, which stores the home directories of regular users.


• `/var` - a place where the system and programs store changing data like databases,caches,etc.. .Inside it we can find a folder called logs containing the records of what the system and programs have done.




# ⌨️ **Keyboard useful combinations**
• `ctrl + l`    ➝ clears terminal

• `Ctrl + Z`	➝equivalent to adding `&` in the end of a command





# 🧠 **Additional notes**
•using `~` meaning I point to the home directory,so instead of writing home i can write `~`
#####  ✏️examples:
	-cd ~

•When I use `ll` or `ls -l`  the first 10 characters make up the permission string:
`-` indicates a file 
`d` indicates a directory 
`r` `w` `x` -stand for read,write,execute
#####  ✏️example:
	 -rwxrwxrwx
	`-` indicates that it's a file(not a directory) we work with 
	first `rwx` stands for the owner's permissions
	second `rwx` stands for the permissions of the group owner of the file
	third `rwx` stands for other users permissions


•A superuser (also known as root) is a special user on Linux and Unix systems with full administrative privileges.

•A reposiroty is a server or location that stores software packages for my system to download and install. APT installs packages from official repositories maintained by my Linux distribution (or trusted third parties like Docker, Node.js, etc.).That means:no shady download links,no sketchy .exe or .deb files,fewer security risks
#####  ✏️example:
	-sudo apt update	➝I should run this so I always have the most updated version of what I want to download
	-sudo apt install firefox	➝APT fetches the Firefox package from a repository on the internet (like http://archive.ubuntu.com), downloads it, and installs it

•PPA = Personal Package Archive.It’s a type of software repository specifically designed for Ubuntu (and Ubuntu-based distros like Linux Mint, Kali, Pop!_OS, etc.).
When I add a PPA to my system, I'm saying: “Hey APT, also check this new place when I install or update software.”.I can use PPA for example if I want to take an application, make some changes to it, host my version somewhere, and install/update it on my system like any other app — using APT.
#####  ✏️example:
	-sudo add-apt-repository ppa:webupd8team/sublime-text-3	➝add the repository pps webupd8team
	-sudo add-apt-repository --remove ppa:webupd8team/sublime-text-3	➝remove the repository pps webupd8team

•GPG (Gnu Privacy Guard) is based on asymmetric cryptography.It's a tool for cryptographic signing and verification.It ensures that software packages or repositories I download are authentic and haven’t been tampered with.When I run apt update or apt install, APT checks the digital signature on packages against the GPG key.If the signature matches, APT trusts the package and installs it.


•Some examples of scripting using bash on the file i created called first_script.sh :

	1. 
	#Defining the Interpreter 
	 #!/bin/bash
	 echo "Hey, what’s your name?"
	read name
	echo "Welcome, $name" 



	2. 
	#Defining the Interpreter 
	#!/bin/bash
	for i in {1..5};
	do
	echo $i
	done   

	
	 
	 3.
	 # Defining the Interpreter 
	#!/bin/bash
	echo "Please enter your name first:"
	read name
	if [ "$name" = "Dani" ]; then
	        echo "Welcome Dani! "
	else
	        echo "Sorry! You are not authorized yo be here!"
	fi 


Then I have to use `chmod +x first_script.sh` to make it executable.I run it with `./first_script.sh`
