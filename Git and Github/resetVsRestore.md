🧠 Understanding the Basics First
In Git, there are three layers:

pgsql
Copy
Edit
1. Working Directory     (your actual files/folder)
2. Staging Area (index)  (what’s ready to be committed)
3. Repository            (what has already been committed)
🔁 git reset vs git restore
Command	Affects	Purpose	Safe?
git restore	Working Directory	Undo changes to files	✅ Safe
git reset	Staging Area & Repo	Unstage, move commits, rewrite history	⚠️ Be careful!
📦 git restore – Restore Files
Used to undo changes in your working directory or unstage a file.

🔹 1. Discard Changes in Working Directory
bash
Copy
Edit
git restore file.txt
🧠 This restores file.txt to the last committed version (undoes local edits).

🔹 2. Unstage a File (if already added with git add)
bash
Copy
Edit
git restore --staged file.txt
🧠 This removes file.txt from the staging area but keeps the changes in the working directory.

🔁 git reset – Reset History or Unstage
🔹 1. Unstage a File
bash
Copy
Edit
git reset file.txt
Same effect as git restore --staged file.txt

🔹 2. Undo the Last Commit (Keep Changes)
bash
Copy
Edit
git reset --soft HEAD~1
🧠 Keeps your changes in staging area, just removes the last commit.

🔹 3. Undo the Last Commit (Unstage Changes)
bash
Copy
Edit
git reset --mixed HEAD~1
🧠 Keeps your changes in working directory, removes commit and unstage.

🔹 4. Undo the Last Commit (Dangerous)
bash
Copy
Edit
git reset --hard HEAD~1
🧠 Deletes your last commit AND discards all changes! ❌ Cannot be undone.

🎯 Use Case Summary
Use Case	Command Example
Unstage a file	git restore --staged file.txt or git reset file.txt
Discard local changes in a file	git restore file.txt
Undo a commit but keep the code	git reset --soft HEAD~1
Undo a commit & unstage code	git reset --mixed HEAD~1
Fully erase commit & code (DANGEROUS)	git reset --hard HEAD~1
⚠️ Pro Tip
Use git reset when dealing with commits and staging area

Use git restore when dealing with file changes only

Never use git reset --hard unless you're 100% sure!