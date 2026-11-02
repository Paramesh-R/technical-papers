# Linux Command Line Interface (CLI) --- Intermediate Cheat Sheet

> A practical reference for everyday Linux use, development work, and
> entry-level technical interviews.

## 1. Navigation

---

Command: Purpose

---

`pwd` Show the current directory

`ls -lstrah` List all files, including hidden
files, with readable sizes

`cd <directory>` Move into a directory

`cd ..` Move to the parent directory

`cd ~` Move to the home directory

`cd -` Return to the previous directory

`tree` Display directories as a tree (if
installed)

---

## 2. Files and Directories

Command: Purpose

---

`touch file.txt` Create an empty file

`mkdir -p a/b/c` Create nested directories

`cp file.txt backup.txt` Copy a file

`cp -r source/ backup/` Copy a directory recursively

`mv old.txt new.txt` Rename or move a file

`rm file.txt` Delete a file

`rm -r directory/` Delete a directory and its contents

`rmdir directory/` Delete an empty directory

`file file.txt` Identify the file type

**Be careful:** `rm` usually does not use a recycle bin. Check paths
before deleting files or directories.

## 3. Viewing File Contents

Command: Purpose

---

`cat file.txt` Display the whole file

`less file.txt` Read a file page by page

`head -n 10 file.txt` Display the first 10 lines

`tail -n 10 file.txt` Display the last 10 lines

`tail -f app.log` Watch new lines added to a log file

`wc -l file.txt` Count lines

`wc -w file.txt` Count words

`wc -c file.txt` Count bytes

## 4. Finding Files and Directories

---

Command: Purpose

---

`find . -name "*.txt"` Find `.txt` names under the current
directory

`find . -type f` Find files recursively

`find . -type d` Find directories recursively

`find . -type f -name "*.log"` Find all `.log` files

`find . -type f -name "*.log" -delete` Delete matching log files

`find ~ -iname "*java*"` Find names containing `java`,
ignoring case

---

## 5. Searching Text with grep

Command: Purpose

---

`grep "error" app.log` Find lines containing `error`

`grep -i "error" app.log` Search without case sensitivity

`grep -n "error" app.log` Show matching line numbers

`grep -r "TODO" .` Search recursively in files

`grep -w "cat" file.txt` Match the whole word

`grep -o "error" app.log` Print only the matching text

`grep -E "error|warning" app.log` Match either pattern

`grep -v "debug" app.log` Show lines that do not match

## 6. Pipes and Redirection

---

Syntax Purpose

---

`command1 \| command2` Pass output of one command as input
to another

`command > output.txt` Write output to a file, replacing
its contents

`command >> output.txt` Append output to a file

`command < input.txt` Read input from a file

`command 2> errors.txt` Redirect error output

`command > output.txt 2>&1` Redirect standard output and errors
to one file

---

**Example:**

```bash
grep -i "error" app.log | wc -l
```

Counts the lines containing `error`, ignoring case.

## 7. Text Processing

---

Command: Purpose

---

`sort names.txt` Sort lines alphabetically

`sort -n numbers.txt` Sort numerically

`sort -r names.txt` Sort in reverse order

`sort names.txt \| uniq` Sort and remove duplicates

`tr 'a-z' 'A-Z'` Convert lowercase to uppercase

`tr -d '0-9'` Remove digits

`sed 's/old/new/g' file.txt` Replace text in output

`awk '{print $1}' file.txt` Print the first
whitespace-separated field

`xargs` Build command arguments from
standard input

---

## 8. Processes

---

Command: Purpose

---

`ps` Show processes attached to the
current terminal

`ps -ef` Display processes in full format

`ps aux` Display detailed process
information

`top` Monitor running processes
interactively

`pgrep firefox` Find process IDs by process name

`pidof firefox` Find process IDs for a program

`pstree` Display parent-child process
relationships

`kill <PID>` Request a process to terminate

`kill -9 <PID>` Forcefully stop a process

`jobs` List jobs started in the current
shell

`command &` Start a command in the background

`fg` Bring a background job to the
foreground

`bg` Resume a suspended job in the
background

`nohup command &` Run a command so it can continue
after terminal logout

---

## 9. Permissions

---

Command: Purpose

---

`ls -l` View permissions and ownership

`chmod +x script.sh` Add execute permission

`chmod 755 script.sh` Set owner to `rwx`, group and
others to `r-x`

`chmod 644 file.txt` Set owner to `rw-`, group and
others to `r--`

`chown user file.txt` Change file owner

`chown user:group file.txt` Change owner and group

`sudo <command>` Run a command with elevated
privileges

---

Permission values: `r = 4` (read), `w = 2` (write), `x = 1` (execute).

## 10. System Information

Command: Purpose

---

`whoami` Show the current username

`hostname` Show the system hostname

`uname -a` Show system and kernel information

`uname -m` Show machine architecture

`lscpu` Show CPU information

`df -h` Show filesystem disk space

`lsblk` List disks and block devices

`lspci` List PCI devices

## 11. Networking

---

Command: Purpose

---

`ip addr` Show network interfaces and IP
addresses

`ip route` Show routing information

`ping <host>` Test network reachability

`hostname -I` Show IP addresses assigned to the
host

`wget <URL>` Download a file from a URL

---

## 12. Basic Package Management (Ubuntu)

Command: Purpose

---

`sudo apt update` Refresh package lists

`sudo apt upgrade` Upgrade installed packages

`sudo apt install <package>` Install a package

`sudo apt remove <package>` Remove a package

`apt search <keyword>` Search for a package

## 13. Useful Shell Shortcuts

Shortcut Purpose

---

`Tab` Auto-complete commands and paths

`Ctrl + C` Interrupt the foreground command

`Ctrl + Z` Suspend the foreground command

`Ctrl + L` Clear the terminal screen

`Ctrl + R` Search command history

`↑` / `↓` Browse command history

## 14. Essential Command Help

Command: Purpose

---

`man <command>` Open the command manual

`<command> --help` Display usage options

`which <command>` Show the executable path

`history` Show previously executed commands

`clear` Clear the terminal display

---
