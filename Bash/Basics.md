# 🐚 Bash - Main: Mastering Bash Commands & Scripting

Welcome to the **ultimate Bash cheatbook**! This guide is designed to help you understand and master all the fundamental and essential Bash commands step by step — from basic terminal usage to scripting and automation.

---

## 🧭 PHASE 1: Bash Basics

### 🔹 1. Bash Environment Commands

| Command         | Description                     |
|----------------|---------------------------------|
| `pwd`          | Print current working directory |
| `whoami`       | Show current user               |
| `clear`        | Clear terminal screen           |
| `exit`         | Exit terminal session           |
| `man <command>`| Open manual for a command       |

```bash
man ls    # Opens manual for the 'ls' command


-------------------------------------------------

✅ Common Wildcards

Wildcard	Description	Example
*	Matches zero or more characters	ls *.txt — all .txt files
?	Matches exactly one character	file?.txt → matches file1.txt, fileA.txt
[abc]	Matches one character in the set	file[123].txt → file1.txt, file2.txt
[a-z]	Matches range	file[a-z].txt
[!abc]	Negation – match anything except a, b, or c	file[!0-9].txt


-------------------------------------------------

 2. File Permissions & Ownership
Every file/directory in Linux has permissions for 3 types of users:


Category	Who?
u	User (owner)
g	Group
o	Others
✅ Permission Types

Symbol	Meaning	Numeric
r	Read	4
w	Write	2
x	Execute	1
-	No permission	0

🔐 View File Permissions

ls -l

Example output:

-rwxr-xr-- 1 shyam staff 1024 Apr 21 script.sh

🔍 Breakdown:

- = regular file

rwx = user has read, write, execute

r-x = group has read and execute

r-- = others have read

✅ Change Permissions

chmod u+x script.sh         # give execute permission to user
chmod 755 script.sh         # rwx for user, rx for group and others
chmod -x file.sh            # remove execute for all

✅ Change Ownership

chown newuser:newgroup file.txt


-------------------------------------------------


3. Process Management (ps, top, kill)

✅ List Running Processes
ps aux                 # All processes
ps -ef                 # Full format
ps -u <username>       # User-specific


✅ Real-Time Process Monitoring
top                   # Shows CPU/memory live
htop                  # (if installed – more visual)

✅ Killing Processes
Command	Description
kill <PID>	Kill by PID
kill -9 <PID>	Force kill
pkill <name>	Kill by name
ps aux | grep python         # find process
kill 1234                    # normal kill
kill -9 1234                 # force kill
pkill chrome                 # kill by name
🔒 Use with caution! Killing critical processes like init, systemd, etc., will crash your system.



-------------------------------------------------


4. Bash Script Creation & Execution

✅ Step 1: Create the Script
nano hello.sh
Add content:


#!/bin/bash
echo "Hello, $USER!"
date

✅ Step 2: Make It Executable
chmod +x hello.sh

✅ Step 3: Run the Script
./hello.sh
OR with interpreter:


bash hello.sh

✅ Script Example with Condition & Loop
#!/bin/bash

echo "Enter a number:"
read num

if [ $num -gt 10 ]; then
    echo "$num is greater than 10"
else
    echo "$num is 10 or less"
fi

for i in {1..5}
do
    echo "Loop $i"
done