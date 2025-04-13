# Git Workflow for Forking and Syncing with Upstream

## Overview

Imagine this setup: you're working on a project that's hosted on GitHub. There’s an original repo (e.g., https://github.com/mainproject/repo) — this is called the **upstream**. You fork it to your GitHub account — it becomes your **origin**. You then clone your fork (your copy) to your local computer — that becomes your **local repo**.

### Relationships
- **origin** → your GitHub fork
- **upstream** → the real/original repo you forked from
- **local** → your cloned version of your GitHub fork

## To Begin Working

1. Clone your fork to your local machine:
    ```
    git clone https://github.com/YOUR-USERNAME/repo.git
    cd repo
    ```

2. Add the upstream remote:
    ```
    git remote add upstream https://github.com/ORIGINAL-OWNER/repo.git
    ```

3. Verify the remotes:
    ```
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
    ```
    git checkout main
    ```

2. Fetch the latest changes from the upstream:
    ```
    git fetch upstream
    ```

3. Merge upstream’s changes into your `main` branch:
    ```
    git merge upstream/main
    ```

Alternatively, you can do this in one step:
```
git pull upstream main
```
This command combines `fetch` + `merge`.

### Resetting Local Changes
If you want your local `main` to exactly match upstream and discard any local changes:
```
git reset --hard upstream/main
```
**Warning**: This is powerful and dangerous — only use it when you're sure you don’t need local commits.

### Update Your Fork on GitHub
To update your forked GitHub repo (origin), push the updated `main` to it:
```
git push origin main
```
This keeps your fork on GitHub in sync with the original upstream repository.

## Working on a New Feature

Once your `main` is up-to-date, you should always create a new branch to add features or make changes. This avoids touching the main branch.

1. Create and switch to a new branch:
    ```
    git checkout -b feature-1
    ```

2. Make your code changes, then:
    ```
    git add .
    git commit -m "Add feature 1"
    ```

3. Push your branch to your fork:
    ```
    git push origin feature-1
    ```

4. Go to GitHub and open a Pull Request:
    - From: `your-username/feature-1`
    - To: `original-owner/main`

This is how you contribute your changes back to the original project.

## Syncing Your Feature Branch with Upstream

If upstream receives new commits while you are working on your feature, sync again:

1. Checkout the main branch:
    ```
    git checkout main
    ```

2. Fetch upstream's changes:
    ```
    git fetch upstream
    ```

3. Merge upstream’s changes into your main branch:
    ```
    git merge upstream/main
    ```

4. Push the changes to your fork:
    ```
    git push origin main
    ```

Now, apply those changes to your feature branch:

1. Checkout your feature branch:
    ```
    git checkout feature-1
    ```

2. Rebase your feature branch on top of the updated main:
    ```
    git rebase main
    ```

This keeps your branch aligned with the latest version of the original project.

## Full Flow Recap

### Setup Remotes (done once)
```
git remote add upstream https://github.com/ORIGINAL-OWNER/project.git
```
```
git checkout main git fetch upstream git merge upstream/main git push origin main
```
```
git checkout -b new-feature
```

```
git push origin new-feature
```

### Open a Pull Request on GitHub
Go to GitHub and open a Pull Request from `your-username/new-feature` to `upstream/main`.

## Terminology
- **origin** = your fork on GitHub
- **upstream** = the original repo
- **git fetch** = get new commits but don’t apply
- **git pull** = get and apply new commits
- **git reset** = forcibly rewrite current branch

## Best Practices:
- Work on new branches
- Keep `main` in sync with upstream
- Rebase your work on top of the latest changes
- Open Pull Requests from your feature branch to upstream/main

