# Linux Interview Questions & Answers

## Linux Commands – Theory

### 1. What is Linux?
Linux is an open-source operating system kernel that forms the basis for various Linux distributions.

### 2. What are the main components of a Linux system?
The main components of a Linux system are the kernel, shell, and file system.

### 3. What is the role of the Linux kernel?
The Linux kernel is the core component of the operating system that manages system resources and provides services to applications.

### 4. What is a shell in Linux?
The shell is a command-line interpreter that allows users to interact with the operating system. It accepts and executes commands.

### 5. What are some popular Linux distributions?
Popular Linux distributions include Ubuntu, Debian, Fedora, CentOS, and Red Hat Enterprise Linux.

### 6. How do you change file permissions in Linux?
The `chmod` command is used to change file permissions in Linux.  
Example: `chmod 755 filename` sets read, write, and execute permissions for the owner and read and execute permissions for others.

### 7. What is the purpose of the `grep` command?
The `grep` command is used to search for specific patterns within files. It is often used for text searching and filtering.

### 8. How do you find files in Linux?
The `find` command is used to search for files and directories in Linux based on various criteria like name, size, and permissions.

### 9. What is the purpose of the `top` command?
The `top` command is used to monitor system processes and resource usage in real-time.

### 10. How do you check the disk usage in Linux?
The `df` command is used to display disk space usage of file systems.

### 11. What is a symbolic link in Linux?
A symbolic link, also known as a soft link, is a special type of file that points to another file or directory.

### 12. What is the purpose of the `tar` command?
The `tar` command is used to create and manipulate archive files, often used for bundling multiple files into a single file.

### 13. How do you start and stop services in Linux?
Service management varies among distributions. In systemd-based systems, you can use:
- `systemctl start service_name`
- `systemctl stop service_name`

### 14. What is the purpose of the `ping` command?
The `ping` command is used to check the connectivity between a source and a destination using ICMP echo requests and replies.

### 15. How do you check the network configuration in Linux?
The `ifconfig` command displays network configuration. In newer systems, it is replaced by the `ip` command.

### 16. What is SSH and how does it work?
SSH (Secure Shell) is a cryptographic network protocol used for secure remote login, command execution, and file transfer. It encrypts communication.

### 17. How do you kill a process in Linux?
The `kill` command is used to terminate a process using PID, or `killall` by process name.

### 18. What is the purpose of the `rsync` command?
The `rsync` command is used for efficient file synchronization and transfer between systems.

### 19. How do you check system hardware information in Linux?
The `lshw` command provides detailed hardware information.

### 20. What is a firewall in Linux?
A firewall is a security mechanism that controls incoming and outgoing network traffic based on rules.

### 21. How do you check the system's IP address in Linux?
The `ip addr` command displays IP addresses assigned to network interfaces.

### 22. What is the purpose of the `cron` daemon?
The `cron` daemon schedules and automates recurring tasks.

### 23. How do you mount a filesystem in Linux?
The `mount` command attaches a filesystem to the directory tree.

### 24. What is the purpose of the `chroot` command?
The `chroot` command changes the root directory for a process.

### 25. How do you compress and decompress files in Linux?
The `gzip` and `gunzip` commands compress and decompress files.

### 26. What is the purpose of the `iptables` command?
The `iptables` command configures the Linux kernel firewall.

### 27. How do you check the CPU usage in Linux?
Use `top`, `htop`, or `mpstat`.

### 28. What is the purpose of the `useradd` command?
The `useradd` command creates user accounts.

### 29. How do you search for a string within files in a directory?
Use `grep -r "string" directory`.

### 30. How do you check the available memory in Linux?
The `free` command shows free and used memory.

---

## Linux Commands – Practical

### 1. ls
List files and directories.  
Example: `ls`

### 2. cd
Change directory.  
Example: `cd /path/to/directory`

### 3. pwd
Print current directory.  
Example: `pwd`

### 4. mkdir
Create directory.  
Example: `mkdir new_directory`

### 5. rm
Remove files/directories.  
Example: `rm file.txt`

### 6. cp
Copy files/directories.  
Example: `cp file.txt /path/to/destination`

### 7. mv
Move or rename files.  
Example: `mv file.txt /path/to/destination`

### 8. touch
Create empty file.  
Example: `touch file.txt`

### 9. cat
Display file content.  
Example: `cat file.txt`

### 10. grep
Search pattern.  
Example: `grep "pattern" file.txt`

### 11. head
Show first lines.  
Example: `head file.txt`

### 12. tail
Show last lines.  
Example: `tail file.txt`

### 13. chmod
Change permissions.  
Example: `chmod 755 file.txt`

### 14. chown
Change ownership.  
Example: `chown user:group file.txt`

### 15. ln
Create symbolic link.  
Example: `ln -s /path/to/file link`

### 16. find
Search files.  
Example: `find /path -name "pattern"`

### 17. tar
Archive files.  
Example: `tar -czvf archive.tar.gz files/`

### 18. unzip
Extract zip files.  
Example: `unzip archive.zip`

### 19. man
Command manual.  
Example: `man ls`

### 20. history
View command history.  
Example: `history`

### 21. ps
View processes.  
Example: `ps aux`

### 22. kill
Terminate process.  
Example: `kill PID`

### 23. df
Disk usage.  
Example: `df -h`

### 24. du
Directory size.  
Example: `du -sh directory`

### 25. scp
Secure copy.  
Example: `scp file.txt user@remote:/path`

### 26. ssh
Remote login.  
Example: `ssh user@host`

### 27. ping
Network test.  
Example: `ping google.com`

### 28. ifconfig
Network info.  
Example: `ifconfig`

### 29. wget
Download file.  
Example: `wget https://example.com/file.txt`

### 30. curl
Transfer data.  
Example: `curl https://example.com`

### 31. top
System monitoring.  
Example: `top`

### 32. apt-get
Debian package manager.  
Example: `apt-get install package`

### 33. yum
RedHat package manager.  
Example: `yum install package`

### 34. systemctl
Service control.  
Example: `systemctl start service`

### 35. journalctl
View logs.  
Example: `journalctl -u service`

### 36. sed
Text replace.  
Example: `sed 's/old/new/' file.txt`

### 37. awk
Text processing.  
Example: `awk '{print $1}' file.txt`

### 38. sort
Sort text.  
Example: `sort file.txt`

### 39. uniq
Remove duplicates.  
Example: `uniq file.txt`

### 40. gzip
Compress file.  
Example: `gzip file.txt`

### 41. gunzip
Decompress file.  
Example: `gunzip file.txt.gz`

### 42. ssh-keygen
Generate SSH keys.  
Example: `ssh-keygen -t rsa`

### 43. ssh-copy-id
Copy SSH key.  
Example: `ssh-copy-id user@host`

### 44. mount
Mount filesystem.  
Example: `mount /dev/sdb1 /mnt`

### 45. umount
Unmount filesystem.  
Example: `umount /mnt`

### 46. lsblk
List block devices.  
Example: `lsblk`

### 47. fdisk
Disk partition.  
Example: `fdisk /dev/sdb`

### 48. date
Show date/time.  
Example: `date`

### 49. echo
Print output.  
Example: `echo "Hello, World!"`

### 50. exit
Exit shell.  
Example: `exit`
