# 🔹 1. What is Git?

**Definition:**  
Git is a version control system (VCS) used to track changes in code/files over time.  
Think of Git like a **"Time Machine"** for your code.

**Why does Git exist?**
- To track who changed what and when.
- To collaborate with others on the same codebase.
- To revert back to any previous version of your project.

---

# 🔹 2. What is Version Control?

**Imagine:**  
You’re writing a document:

- You make Version 1.
- Then Version 2 with some changes.
- Then Version 3...

**You want to:**
- Go back to Version 1? ✅  
- Know what changed from Version 1 to 2? ✅  
- Collaborate with someone else on Version 2 without messing up your copy? ✅  

This is what version control systems do!

---

# 🔹 3. Git vs GitHub

| Git | GitHub |
|-----|--------|
| Software/tool installed locally | Online platform (hosted on the web) |
| Used to track changes in code | Used to store Git repositories online |
| Works offline | Needs internet |
| You push your code to GitHub | GitHub receives your pushed code |
| No user interface (command line) | Has web interface (GitHub.com) |

**Analogy:**  
Git = Your notebook where you write versions  
GitHub = Cloud backup of your notebook

---

# 🔹 4. How Git Works (Core Concepts)

## 🧠 Git Internals – In Simple Terms
Git works on **snapshots**, not differences.  
Every time you commit, Git takes a snapshot of all your files (efficiently).  
Git stores these snapshots as objects in a local `.git` folder.

### Key Concepts

| Concept | Meaning |
|---------|---------|
| Repository (repo) | A Git-managed project directory |
| Commit | A saved version of your project |
| Branch | A separate version of your project to test new features |
| Merge | Combining two branches |
| Clone | Copying a remote repo to your local system |
| Push | Uploading commits to GitHub |
| Pull | Downloading new changes from GitHub |
| Staging Area | Where changes wait before being committed |

---

# 🔹 5. Installing Git

✅ **Steps:**
1. Download Git from: [https://git-scm.com/](https://git-scm.com/)
2. Install it and use:


git --version


# Step 1: Initialize Git in your project folder
git init

# Step 2: Track changes
git add filename_or_dot

# Step 3: Save a snapshot (commit)
git commit -m "Your message here"

# Step 4: Connect to GitHub repo (first time only)
git remote add origin https://github.com/username/repo-name.git

# Step 5: Push your local code to GitHub
git push -u origin main

<<<<<<< HEAD
# Step 6: Undo Stage
git reset HEAD file.txt

# Save Changes for later
git stash
=======
# Key points
1. The mechanism that Git uses for this checksumming is called a SHA-1 hash.This is a 40-character
string composed of hexadecimal characters (0–9 and a–f) and calculated based on the contents of a
file or directory structure in Git

2. You can view all of your settings and where they are coming from using:
   $ git config --list --show-origin

3. $ git config --global user.name "John Doe"
   $ git config --global user.email johndoe@example.com

4. git add -h

5. you can use git diff before adding files to see the changes in your working directory that aren't yet staged. 
   You can also see the diff of staged changes by using git diff --staged or git diff --cached

6. Before a commit, you need to "stage" those changes using git add. This command moves the changes from your working directory to the staging area (also known as the index). 

7. Temporarily switch to a different commit
   If you want to temporarily go back to it, fool around, then come back to where you are, all you have to do is check out the desired commit:

# This will detach your HEAD, that is, leave you with no branch checked out:
  git checkout 0d1d7fc32

8. Or if you want to make commits while you're there, go ahead and make a new branch while you're at it:
   git checkout -b old-state 0d1d7fc32

9. Reverting Working Copy to Most Recent Commit
    To revert to the previous commit, ignoring any changes:

    git reset --hard HEAD
>>>>>>> 081fb8e17ccd2620c382ef210fa3f8bc592bb929
