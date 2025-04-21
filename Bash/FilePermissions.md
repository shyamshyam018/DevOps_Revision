Bash: File Permissions & Ownership — In Depth
🔸 1. What Are File Permissions?
In Linux, every file and directory has permissions associated with it that define who can read, write, or execute it.

Permissions are managed for three categories of users:


Symbol	User Type
u	User (Owner)
g	Group
o	Others (Everyone else)
a	All (u + g + o)

🔸 2. Understanding ls -l Outpu
ls -l
Output example:

diff
Copy
Edit
-rwxr-xr--  1 shyam  devs  1200 Apr 20 10:30  deploy.sh
Breakdown:

Field	Meaning
-rwxr-xr--	Permissions (rwx for user, etc.)
1	Link count
shyam	File owner (user)
devs	Group
1200	File size in bytes
Apr 20 10:30	Last modified
deploy.sh	File name
🔤 Permission Code Explained:
pgsql
Copy
Edit
- rwx r-x r-- 
| |   |   |
| |   |   └── Others: Read only
| |   └────── Group: Read + Execute
| └────────── User: Read + Write + Execute
└──────────── File type (- = file, d = dir)
🔸 3. Permission Bits and Numeric (Octal) Format
Each permission (read/write/execute) has a numeric value:


Permission	Symbol	Value
Read	r	4
Write	w	2
Execute	x	1
None	-	0
🧮 Example:
rwxr-xr-- = 7 5 4 (User=7, Group=5, Others=4)


So, this is:
chmod 754 file.sh
🔸 4. Changing Pe
rmissions — chmod
✅ Symbolic Forma
chmod u+x script.sh       # Add execute for user
chmod g-w file.txt        # Remove write from group
chmod o=r file.t
xt        # Set others to read-only
✅ Numeric Forma
chmod 755 script.sh       # rwx for user, rx for group/others
chmod 644 notes.txt       # rw for user, r for group/others
chmod 700 secret.sh       # Full for user, none for others

Number	Meaning
7	Read, write, execute
6	Read, write
5	Read, execute
4	Read only
0	No permission
🔸 5. Special Permissions
✅ SetUID (Set User ID) — 4xxx

Executes file with the owner's permissions (used in passwd)
chmod 4755 file
✅ SetGID (Set Group ID) — 2xxx

Executes file with the group’s permissions, or in directories, new files get the directory’s group.
chmod 2755 file_or_dir
✅ Sticky Bit — 1xxx

Used in shared directories (like /tmp) so only the file owner can delete.
chmod 1777 /shared/folder

Example with all special bits
chmod 4775 my_script  # SetUID + rwx for user, rx for others
🔸 6. Changing
 Ownership — chown, chgrp
✅ Change Owne
chown newuser file.txt

✅ Change Owner and Grou
chown newuser:newgr
oup file.txt
✅ Change Group Onl
chgrp newgroup file.txt
🔸 7. Default Permissions: umask
umask controls the default permission set for new files or folders.


File Default	666 (rw-rw
-rw-)
Dir Default	777 (rwxrwxrwx
umask 022     # Default file: 644
, directory: 755
To make files private by default:
umask 077     # Files: 600, Dirs: 700
🔸 8. Permissions for Directories

Permission	Meaning
r	Can list files inside
w	Can add/remove files
x	Can
 enter the directory (cd)
Example
chmod 700 mydir     # Private directory
chmod 755 public    # Accessible to all
🧠 Pro Tips
Use ls -ld <dir> to check directory permissions

Use chmod -R 755 dir/ to apply changes recursively

Use stat filename to get detailed metadata


Use find to batch change permissions:
find . -type f -exec chmod 644 {} \;
find . -type d -exec chmod 755 {} \;
🔐 Real-World Use Cases

✅ Make a shell script executable for your user:
chmod u+x deploy.sh

✅ Secure sensitive files:
chmod 600 ~/.ssh/id_rsa

✅ Allow only owner to enter config folder:
chmod 700 /etc/myconfig/