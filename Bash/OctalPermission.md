Understanding Numeric (Octal) File Permissions in Linux
🔸 1. Permission Basics
Each of the three basic file permissions has a binary and numeric value:


Permission	Symbol	Binary	Octal Value
Read	r	100	4
Write	w	010	2
Execute	x	001	1
No Permission	-	000	0
📚 These are bit flags:
Each permission is a bit in a 3-bit binary number.

The final number is calculated as: read (4) + write (2) + execute (1)

🔸 2. Mapping Octal → Symbolic Permissions
Example: chmod 754 file.sh

User Type	Octal Value	Binary	Permissions
User	7	111	rwx
Group	5	101	r-x
Others	4	100	r--
So the string output in ls -l would look like:

-rwxr-xr-- 1 user group 1234 Apr 21 14:23 file.sh
🔸 3. Common Octal Permission Codes

Octal	Symbolic	Meaning
777	rwxrwxrwx	Full access for everyone
755	rwxr-xr-x	Full for owner, read/exec for others
700	rwx------	Only owner can access
644	rw-r--r--	Owner can edit, others can only read
600	rw-------	Private file
444	r--r--r--	Read-only for all
000	----------	No access at all
🔸 4. Converting Between Symbolic and Octal
Let’s break this down like a mini calculator.

✅ Symbolic ➡ Octal
Say you have:

-rw-r--r--
Break into 3 groups:

rw- → 4 (r) + 2 (w) = 6

r-- → 4 = 4

r-- → 4 = 4

So, octal is:

chmod 644 file.txt
✅ Octal ➡ Symbolic
Say you have chmod 751:

7 → rwx

5 → r-x

1 → --x

So, symbolic is:

-rwxr-x--x
🔸 5. How This Relates to Regex-Style Permission Strings
The 10-character string in ls -l looks like this:

-rwxr-xr--

Position	Meaning
1	Type (- for file, d for dir)
2-4	User permissions (rwx)
5-7	Group permissions (r-x)
8-10	Other permissions (r--)
If you convert positions 2–10 into binary and map them as a 9-bit binary, you can directly compute the octal.

🧠 Formula to Convert from Symbolic to Octal:
Take each triplet:

rwx → 111 → 7

rw- → 110 → 6

r-- → 100 → 4

Then combine them to form your octal:

chmod 764 myfile
🔸 6. Practice Examples
Example 1:
chmod 751 my_script.sh
User: 7 → rwx

Group: 5 → r-x

Others: 1 → --x

Symbolic: -rwxr-x--x

Example 2:
chmod 600 private.txt
User: 6 → rw-

Group: 0 → ---

Others: 0 → ---

Symbolic: -rw-------

🔸 7. Special Bits Reminder (Advanced)

Bit	Octal	Meaning	Used For
SetUID	4	Run as file owner	chmod 4755
SetGID	2	Run as group or inherit it	chmod 2755
Sticky	1	Only owner can delete file	chmod 1777 /tmp
✅ TL;DR Cheatsheet

Symbolic	Octal	Description
rwx	7	Read + Write + Execute
rw-	6	Read + Write
r-x	5	Read + Execute
r--	4	Read only
--x	1	Execute only
---	0	No permissions