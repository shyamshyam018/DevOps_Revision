# 🔄 Recovering Deleted Files in Git

## 🚨 Scenario 1: File Deleted Locally (Still in Remote Repo)

If you accidentally deleted a file **locally**, but it's still in the **remote repository**, you can restore it from your last commit:

```bash
# For all Git versions
git checkout HEAD -- path/to/your/file

# If using Git 2.23 or newer
git restore path/to/your/file

To list all files currently in the staging area, use:
git ls-files




## 🚨 Scenario 2: File Deleted, Committed, and Pushed

If you've deleted the file, committed the deletion, and pushed it, you can still bring it back from a previous commit:

Find the commit that had the file
git log -- path/to/your/file

Restore the file from that commit
git checkout <commit_hash>^ -- path/to/your/file

Add and commit the file again   
git add path/to/your/file

git commit -m "Restore accidentally deleted file"
git push

To list all files currently in the staging area, use:
git ls-files

