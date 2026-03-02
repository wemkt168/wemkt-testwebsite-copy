---
description: Automatically stage, commit, and push changes to GitHub to trigger deployments (e.g., Zeabur).
---

This workflow ensures that all local changes are safely committed and pushed to the remote repository. It is designed to be run at the end of a development cycle or when a specific feature is completed.

1.  **Check Status**
    View the current git status to understand what will be committed.
    `git status`

2.  **Stage All Changes**
    Add all modified and new files to the staging area.
    `git add .`

// turbo
3.  **Commit and Push**
    Commit with a generic but descriptive message (user can override if running manually) and push to the current branch.
    `git commit -m "chore: auto-sync changes via workflow" && git push`

4.  **Verify Push**
    Confirm that the push was successful.
    `git log -1 --stat`
