---
layout: post
title: Linux File System and Commands
date: 2026-02-05
description: a list of Linux commands and an overview of the Linux File System
tags: tools-and-commands
categories: cybersecurity
giscus_comments: false
related_posts: true
pretty_table: true
toc:
  beginning: true
---

## The Linux File System
An overview of the Linux File System

* The Linux File System
  * the directory structure Linux uses to store, organize, and access files
  * Everything in Linux is treated as a file, such as
    * programs, logs, devices, configs, network interfaces

#### Key Linux Directories

| Directory | What is Inside | Purpose | Why it Matters | What to Look For
| :--  | :------------  | :------------ | 
| `/`  | All system directories | the root of the file system | It's the starting point |
| `/home`  | User home folders, user files | for storing non-root user data | Look for SSH keys, configs, flags | `.ssh/id_rsa`, `.bash_history`
| `/root`  | Root user's home directory | for admin (root) account files | If you have access, you gain control of the full system | flags, sensitive configurations
| `/etc`  | Configuration files | for system-wide configurations | users, passwords, sudo rules | `passwd`, `shadow`, `sudoers`
| `/bin`  | Essential system commands | for core binaries needed by all users | users, passwords, sudo rules | SUID binaries for privilege escalation
| `/sbin`  | System admin binaries | for Admin-level system tools | Often abused if misconfigured | admin binaries
| `/usr/bin`  | User programs and utilities | for installed user-level binaries | Abusable binaries, PATH hijacking | abusable binaries
| `/usr/sbin`  | Admin tools (non-essential) | for advanced system management | Possible SUID or weak permissions | system tools
| `/var`  | Logs, caches, spool files | for variable run time data | Log anaalysis, log poisoning, credentials | logs
| `/var/log`  | Systems and application logs | for storing logs | Auth logs, web logs, forensic clues | `auth.log`, `access.log`
| `/tmp`  | Temporary files | for short-lived, world-writable storage | Upload payloads, execute scripts | uploaded payloads
| `/dev`  | Device files | Interface for the hardware | Used in reverse shells and I/O redirection | `/dev/tcp`, `/dev/tty` for reverse shells
| `/proc`  | Process and system information | Virtual file system | Leak environment variables, running processes | `env` varriables, process info
| `/opt`  | Optional/third-party software | External applications | Often poorly secured custom apps | custom apps, scripts
| `/lib`  | Shared libraries | Libraries required by binaries | Library hijacking attacks |
| `/mnt`  | Mountd file systems | for temporary mount points | Access external or mounted drives | mounted drives
| `/media`  | Removable media | USBs, CDs, external devices | Data leakage opportunities | removable storage
| `/srv`  | Service data | for data served by services | Web or FTP content |
| `/var/www`  | Web server files | Website content | Web shells, source code leaks | website source code, configuration files
| `/boot`  | Bootloader files | for System boot data | Rare target; kernel attacks | kernel files
| `/run`  | Runtime process data | for storing temporary system information | Rare target; kernel attacks | sockets and sessions
| `/lost+found`  | Recovered files | for file system recovery | For looking at discarded or recovered files |

<br>

---

## Linux Commands
An overview of some Linux commands organized by use

<br>

### General Commands
An overview of some generic Linux commands

#### Navigation Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ |
| `pwd`  | Shows current directory | For orientation to see where I am | 
| `cd`  | Changes directory | Moving around the filesystem | `cd [directory]` <br> `cd ..` → go up one level <br> `cd ~` → go to home directory <br> `cd /` → go to root
| `man`  | Shows command manuals | For providing command documentations for options and usage explanations |
| `ls` | Shows detailed listing of the directories | For checking permissions | `ls -la`
| `tree`  | Shows the directory structure | For visual recon |


<br>

#### Searching & Filtering Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `grep` | Search text | For finding credentials | `grep "root" /etc/passwd` <br> `grep -R "password" /etc` → recursive search
| `find`  | Finding files | For looking and hunting for loots | `find / -name "*.conf"`
| `locate`  | Finding files using a databse | For searching files quickly | `locate [filename]`


<br>

#### File Creating, Viewing, Editing, and Management Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ |
| `cp`  | Copy contents of files | For quick duplicates | `cp [source file] [destination file]`
| `mv`  | Moves files/ renames files | For renaming/moving files | `mv [old_name] [new_name]`
| `rm`  | Deletes files or directories | For deleting to cause unavailability | `rm [old_name]` or `rm -r [directory name]`
| `mkdir`  | Creates directory | For creating directories | `mkdir [directory name]`
| `rmdir`  | Deletes **empty** directories | For deleting empty directories | `rmdir [directory name]`
| `nano`  | Terminal text editor | For editing writable files | `nano [filename]`
| `vi/wim`  | Advanced text editor | For editing writable files, common on servers | `vim [filename]`
| `touch`  | Creates empty files | For creating new files instantly, also updates file timestamps | `touch [filename]`
| `echo`  | Write text to a file | For scripting | `echo "hi" > [filename]` → writing text to a file <br> `echo "hi" >> [filename]` → appending text to a file (persistent)
| `cat`  | Prints entire file | For viewing **small** files | `cat [filename]` 
| `less`  | Displays a scrollable viewer of a file | For viewing **large** files | `less [filename]`
| `head`  | Displays the first 10 lines of a file | For a quick preview | `head [filename]`
| `tail`  | Displays the last lines of a file and live logs | For monitoring logs | `tail -f [filename]`

<br>

#### File Transfers, Downloads, and Payloads Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `wget` | Downloads files | For downloading files and even payloads | `wget [url]`
| `curl` | Fetches data | For reverse shells | `curl [url]`

<br>

#### Networking & Services Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `ip a` | Shows network interfaces | For looking at the whole network |
| `ss` | For showing listening services | For looking at local ports | `ss -tulpn` or `netsat -tulpn` (older version)
| `arp` | For showing neighboring networks | For lateral movement | `arp -a` 

<br>

---

### Penetration Testing Commands
An overview of the most commonly used commands in penetration testing engagements

<br>

#### System & User Enumeration Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `whoami` | Shows current user | For checking privilege level |
| `hostname`  | Shows system name | For target identification | 
| `id`  | Shows User ID, groups | For sudo/group abuse |
| `uname`  | Shows kernel information | For checking Kernel exploits | `uname -a`
| `lsb_release`  | Shows OS version | To match exploits to use | `lsb_release -a`
| `uptime`  | Shows system runtime | For checking stability |
| `ps`  | Displays running processes | For showing active processes to monitor system activity |
| `du`  | Shows directory sizes | For finding large data | `du -sh *`

<br>

#### User & Home Directory Recon 

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `ls /home` | Shows users | For finding targets |
| `ls -la ~`  | Shows hidden files | For looking for SSH keys, history | 
| `cat ~/.bash_history`  | Shows command history | For looking for credentials, tools |
| `find /home -name "*.txt"`  | For finding files | For looking for flags and notes |

<br>

#### Looking for Credentials Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `cat /etc/passwd` | Shows users | For finding valid accounts |
| `cat /etc/shadow` | Shows password hashes | For offline tracking |
| `env`  | Shows environment variables | For looking for API keys, tokens | 

<br>

#### Permissions & Ownerships Commands

| Command | What it Does | Purpose | Example
| :--  | :------------  | :------------ | 
| `chmod` | Changes permissions | For executing payloads | `chmod +x script.sh`
| `chown` | Changes owner | For persisting attacks | `chown root:root file`
| `ls -l`  | Views permissions | For finding weak files | 

<br>

 




