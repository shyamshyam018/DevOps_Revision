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
