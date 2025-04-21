
# 🌱 Git Master Notes

## 📁 Git Basics

### Initialize a Git Repository
```bash
git init
```
- Creates a hidden `.git` folder in your directory.
- To view hidden files:  
  ```bash
  ls -a
  ```
- To list contents inside `.git`:
  ```bash
  ls .git
  ```

Contents typically include:
- `HEAD`, `config`, `objects`, `refs`, `info`, `description`, `hooks`

---

## 💾 Commits and Reset

### Reset to a Specific Commit
```bash
git reset <commit-hash>
```
- Soft reset: Keep changes in the working directory
- Hard reset: Remove changes and reset working directory to the commit
```bash
git reset --hard <commit-hash>
```

---

## 🛠 Stashing Changes

### Save Changes for Later
```bash
git stash
```
- Stashes your current changes so you can work on something else.

### Retrieve Stashed Changes
```bash
git stash pop
```
- Pops the latest stash back into your working directory.

### Clear All Stashes
```bash
git stash clear
```

---

## 🌐 Remote Repositories

### View Remote Repositories
```bash
git remote -v
```
- Shows the remote repositories connected to your current project.

### Push Changes to Remote Repository (Force Push)
```bash
git push origin main -f
```
- Force push to remote if you've made commits locally but the remote has diverged.

---

## 🔄 Branching and Merging

### Create and Checkout a New Branch
```bash
git branch feature-1
git checkout feature-1
```
- `feature-1` is the new branch.

### Merge Conflicts and Squash Commits

To merge commits before pushing:
```bash
git rebase -i <commit-hash>
```
- Use `pick` for commits you want to keep.
- Use `squash` to combine commits.

To resolve merge conflicts during rebase, choose the desired version and continue:
```bash
git rebase --continue
```

### Fetch and Reset to Upstream
To maintain the upstream changes:
```bash
git checkout main
git fetch --all --prune
git pull upstream main
git reset --hard upstream/main
```

---

## 🚀 Other Tips

### Forked Repositories
The original repository from where you've forked is called the "upstream" repository. Always make sure your local copy is in sync with the upstream before pushing new changes.

---

## 💡 Edge Cases

### When to Force Push
Force pushing (`git push -f`) should be used when:
- You have committed changes to the local branch that conflict with changes in the remote repository.
- It can overwrite changes on the remote branch, so use with caution.

### Handling Merge Conflicts
During rebase or merge:
- Edit conflicting files.
- After resolving, use:
  ```bash
  git add <file>
  git rebase --continue
  ```
- If you want to cancel the rebase:
  ```bash
  git rebase --abort
  ```

---

## 📚 Useful Commands

### View Commit History
```bash
git log --oneline
```

### View Changes in Staged Files
```bash
git diff --staged
```

### Revert a Commit
```bash
git revert <commit-hash>
```

### Delete a Branch
```bash
git branch -d feature-1
```

### List All Branches
```bash
git branch
```
