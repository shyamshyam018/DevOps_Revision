# ✅ Git Branching and Merging Notes

## 🔀 Step 7: `git branch` – Work on Features Separately

### 📘 What it does:
The `git branch` command lets you:
- List all branches
- Create a new branch
- Delete a branch

Branches are used to work on different features or fixes **without affecting the main code**.

### 🧪 Examples:
```bash
git branch             # Show all local branches
git branch feature-1   # Create a new branch named 'feature-1'
git checkout feature-1 # Switch to the 'feature-1' branch
git checkout main      # Switch to the main branch
git merge feature-1    # Merge 'feature-1' into 'main'
