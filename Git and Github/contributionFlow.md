# Git Workflow for Forking and Syncing with Upstream

Imagine this setup: you're working on a project that's hosted on GitHub. There’s an original repo (e.g., https://github.com/mainproject/repo) — this is called the **upstream**. You fork it to your GitHub account — it becomes your **origin**. You then clone your fork (your copy) to your local computer — that becomes your **local repo**.

## Relationships
- **origin** → your GitHub fork
- **upstream** → the real/original repo you forked from
- **local** → your cloned version of your GitHub fork

## To begin working:

1. Clone your fork to your local machine:
    ```bash
    git clone https://github.com/YOUR-USERNAME/repo.git
    cd repo
    ```

2. Add the upstream remote:
    ```bash
    git remote add upstream https://github.com/ORIGINAL-OWNER/repo.git
    ```

3. Verify the remotes:
    ```bash
    git remote -v
    ```
    The output should show:
    ```
    origin    https://github.com/YOUR-USERNAME/repo.git (fetch)
    upstream  https://github.com/ORIGINAL-OWNER/repo.git (fetch)
    ```

## Keeping Your Fork Updated

Over time, the upstream repo might get updated by the original maintainers, while your fork and your local copy become outdated. To keep everything updated:

1. Checkout the `main` branch:
    ```bash
    git checkout main
    ```

2. Fetch the latest changes from the upstream:
    ```bash
    git fetch upstream
    ```

3. Merge upstream’s changes into your `main` branch:
    ```bash
    git merge upstream/main
    ```

Alternatively, you can do this in one step:
```bash
git pull upstream main


Update Your Fork on GitHub
To update your forked GitHub repo (origin), push the updated main to it:

bash
Copy
Edit
git push origin main
This keeps your fork on GitHub in sync with the original upstream repository.

Working on a New Feature
Once your main is up-to-date, you should always create a new branch to add features or make changes. This avoids touching the main branch.

Create and switch to a new branch:

bash
Copy
Edit
git checkout -b feature-1
Make your code changes, then:

bash
Copy
Edit
git add .
git commit -m "Add feature 1"
Push your branch to your fork:

bash
Copy
Edit
git push origin feature-1
Go to GitHub and open a Pull Request:

From: your-username/feature-1

To: original-owner/main

This is how you contribute your changes back to the original project.

Syncing Your Feature Branch with Upstream
If upstream receives new commits while you are working on your feature, sync again:

Checkout the main branch:

bash
Copy
Edit
git checkout main
Fetch upstream's changes:

bash
Copy
Edit
git fetch upstream
Merge upstream’s changes into your main branch:

bash
Copy
Edit
git merge upstream/main
Push the changes to your fork:

bash
Copy
Edit
git push origin main
Now, apply those changes to your feature branch:

Checkout your feature branch:

bash
Copy
Edit
git checkout feature-1
Rebase your feature branch on top of the updated main:

bash
Copy
Edit
git rebase main
This keeps your branch aligned with the latest version of the original project.

Full Flow Recap
Setup Remotes (done once)
bash
Copy
Edit
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git
Sync Your Fork
bash
Copy
Edit
git checkout main
git fetch upstream
git merge upstream/main
git push origin main
Start Feature Work
bash
Copy
Edit
git checkout -b new-feature
# Make changes, commit
git push origin new-feature
Open a Pull Request on GitHub
Go to GitHub and open a Pull Request from your-username/new-feature to upstream/main.

Terminology
origin = your fork on GitHub

upstream = the original repo

git fetch = get new commits but don’t apply

git pull = get and apply new commits

git reset = forcibly rewrite current branch

Best Practices:
Work on new branches

Keep main in sync with upstream

Rebase your work on top of the latest changes

Open Pull Requests from your feature branch to upstream/main
