Imagine this setup: you're working on a project that's hosted on GitHub. There’s an original repo (e.g., https://github.com/mainproject/repo) — this is called the upstream. You fork it to your GitHub account — it becomes your origin. You then clone your fork (your copy) to your local computer — that becomes your local repo.

So the relationships are:
origin → your GitHub fork  
upstream → the real/original repo you forked from  
local → your cloned version of your GitHub fork

To begin working:
git clone https://github.com/YOUR-USERNAME/repo.git  
cd repo  
git remote add upstream https://github.com/ORIGINAL-OWNER/repo.git  
git remote -v  

The output should show:  
origin    https://github.com/YOUR-USERNAME/repo.git (fetch)  
upstream  https://github.com/ORIGINAL-OWNER/repo.git (fetch)

Over time, the upstream repo might get updated by the original maintainers, while your fork and your local copy become outdated. To keep everything updated:

git checkout main  
git fetch upstream  
git merge upstream/main  

Alternatively, you can do:  
git pull upstream main  

This command combines `fetch` + `merge`.

If you want your local `main` to exactly match upstream and discard any local changes:
git reset --hard upstream/main  

This is powerful and dangerous — only use it when you're sure you don’t need local commits.

Now, to update your forked GitHub repo (origin), push the updated `main` to it:  
git push origin main

This keeps your fork on GitHub in sync with the original upstream repository.

Once your main is up-to-date, you should always create a new branch to add features or make changes. This avoids touching the main branch.

git checkout -b feature-1  

This creates and switches to a new branch named `feature-1`.

Make your code changes, then:  
git add .  
git commit -m "Add feature 1"

Now push your branch to your fork:
git push origin feature-1

Then go to GitHub and open a Pull Request:
From: your-username/feature-1  
To: original-owner/main

This is how you contribute your changes back to the original project.

If upstream receives new commits while you are working on your feature, sync again:

git checkout main  
git fetch upstream  
git merge upstream/main  
git push origin main  

Then, apply those changes to your feature branch:
git checkout feature-1  
git rebase main  

This keeps your branch aligned with the latest version of the original project.

To recap the full flow:

# Setup remotes (done once)
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git

# Sync your fork
git checkout main  
git fetch upstream  
git merge upstream/main  
git push origin main

# Start feature work
git checkout -b new-feature  
# make changes, commit  
git push origin new-feature

# Go to GitHub and open a PR to upstream

Terminology:
origin = your fork on GitHub  
upstream = the original repo  
git fetch = get new commits but don’t apply  
git pull = get and apply new commits  
git reset = forcibly rewrite current branch  

Always:
- Work on new branches
- Keep `main` in sync with upstream
- Rebase your work on top of the latest changes
- Open Pull Requests from your feature branch to upstream/main
