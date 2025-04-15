CHAT PROMPT LINK - https://chatgpt.com/c/67f93942-1788-8003-afbf-64d32c290b2c

1. What is the difference between origin and upstream?
Answer:

origin: Refers to your fork on GitHub.

upstream: Refers to the original repository you forked from.

2. How do you add the original repo as an upstream remote?
Command:

git remote add upstream https://github.com/ORIGINAL-OWNER/repo.git
Usage: Use this when you've forked a repo and want to track the original one for updates.

3. How can you view all the remotes for a project?
Command:

git remote -v
Usage: To verify that origin and upstream are correctly set.

4. How do you bring the latest changes from upstream into your local repo?
Command:

git fetch upstream
git checkout main
git merge upstream/main
Alternative (Shortcut):

git pull upstream main
Usage: Use this when you want to sync your local main with the latest changes from the original repository.

5. How do you update your forked GitHub repo after syncing your local main?
Command:

git push origin main
Usage: Pushes your local main (now up to date) to your GitHub fork (origin).

6. What should you do before starting work on a new feature?
Command:

git checkout -b feature-branch-name
Usage: Always create a new branch off of main before making any feature-specific changes.

7. How do you save your work in Git after modifying files?
Commands:

git add .
git commit -m "Your message here"
Usage:

git add . stages all changes.

git commit saves them with a message describing what you changed.

8. How do you push your new feature branch to your GitHub fork?
Command:

git push origin feature-branch-name
Usage: After committing your changes locally, use this to upload the branch to GitHub.

9. What is the next step after pushing a feature branch to GitHub?
Answer: Go to GitHub and open a Pull Request from:

your-username/feature-branch → upstream/main
10. What if the upstream/main gets new changes while you're working on your feature branch?
Step-by-step Commands:

git checkout main
git fetch upstream
git merge upstream/main
git push origin main
Then update your feature branch:

git checkout feature-branch
git rebase main
Usage: Keeps your feature branch aligned with the latest main branch updates.

11. What is the purpose of git rebase in this case?
Answer: git rebase main re-applies your feature branch commits on top of the updated main, creating a cleaner history.

12. How do you forcibly reset your local main to match upstream exactly?
Command:

git reset --hard upstream/main
Usage: Use with caution. It deletes any local commits and makes your branch an exact copy of upstream/main.

13. How to completely sync your forked repo (origin) from upstream?
Step-by-step:

git checkout main
git fetch upstream
git merge upstream/main
git push origin main
Usage: Makes both your local and your forked GitHub repo up to date with the original project.

14. What's the difference between git fetch, git pull, and git merge?
Answer:

git fetch: Gets the latest commits but doesn’t apply them.

git pull: Gets and merges the latest commits in one step.

git merge: Applies fetched changes manually if you used git fetch earlier.

15. When should you use git pull vs. git fetch + git merge?
Answer: Use git pull for convenience when you trust upstream changes.
Use git fetch + git merge when you want to inspect or review changes before merging.

