# Git Collaboration Workflow: Fork, Clone, Push, PR, Review, Merge

## Understanding Remotes
- `origin` refers to the central remote repository (GitHub, GitLab, etc.).
- `origin/master` is the master branch of the remote repository.
- `origin/branch_name` refers to a specific branch on the remote.
- `git remote -v` → View configured remotes.
- `git branch -vv` → Check if your local branch is behind the remote.

---

## Forking & Cloning
1. **Fork the repository** → Since you don't have push access to the original repository.
2. **Clone the forked repository**
   ```sh
   git clone <forked_repo_url>
   ```
3. **Set upstream to the original repository**
   ```sh
   git remote add upstream <original_repo_url>
   ```
4. **Fetch upstream changes**
   ```sh
   git fetch upstream
   git merge upstream/master  # Merge upstream changes into your local master
   ```

---

## Pushing Changes & Pull Requests
1. **Create a new branch for changes**
   ```sh
   git switch -c feature-branch
   ```
2. **Make changes & commit**
   ```sh
   git add .
   git commit -m "Description of changes"
   ```
3. **Push to forked repository**
   ```sh
   git push origin feature-branch
   ```
4. **Open a Pull Request (PR)** on GitHub/GitLab:
   - Navigate to your forked repository.
   - Click **New Pull Request**.
   - Select `feature-branch` and compare with `upstream/master`.
   - Add a description and request reviewers.
   - Submit the PR.

---

## Reviewing & Merging a PR
1. **Reviewer receives a notification** → They review and request changes.
2. **Address feedback** → Make new commits, push changes.
3. **Reviewer approves the PR** → Ready for merging.
4. **Merge the PR**:
   - **Standard merge** → Preserves commit history.
   - **Squash merge** → Combines commits into one.
   - **Rebase merge** → Replays changes onto the latest commit in `master`.
5. **Post-merge cleanup**:
   ```sh
   git remote prune origin  # Remove deleted remote branches
   git branch -d feature-branch  # Delete local branch
   ```

---

## Pulling & Syncing Changes
- `git pull` → Fetch + merge remote changes.
- `git pull --rebase` → Replays local changes on top of remote changes (avoids merge commits).
- Store credentials:
  ```sh
  git config --global credential.helper cache
  ```

---

## Sharing Tags
- Tags are not shared by default. Push them manually:
  ```sh
  git push origin <tag_name>
  ```
- Delete a remote tag:
  ```sh
  git push origin --delete <tag_name>
  ```

---

## Managing Remote Branches
- `git branch -r` → Show remote tracking branches.
- `git push --set-upstream origin <branch_name>` → Push a branch to remote.
- `git push -d origin <branch_name>` → Delete a remote branch.
- `git branch -d <branch_name>` → Delete a local branch.

---

## Handling Remote Tracking Branches
- If you fetched changes but the branch does not exist locally:
  ```sh
  git switch -c <local_branch_name> origin/<remote_branch>
  ```
- To clean up remote tracking branches:
  ```sh
  git remote prune origin
  ```

---

## Issue Tracking & Milestones
1. **Create an issue** → Title, description, labels, and assign it.
2. **Labels** → Categorize issues (e.g., `bug`, `enhancement`, `refactoring`).
3. **Milestones** → Group issues under a deadline.
4. **Link issues to PRs** → Track progress.

---

## Summary of Key Commands

| Command | Description |
|---------|-------------|
| `git clone <url>` | Clone a repository |
| `git fetch origin master` | Fetch `master` branch changes from remote |
| `git pull` | Fetch + merge changes from remote |
| `git push origin master` | Push `master` branch to remote |
| `git push` | Shortcut for `git push origin master` |
| `git push origin <tag>` | Push a tag to remote |
| `git push -d origin <branch>` | Remove a branch from remote |
| `git remote add upstream <url>` | Add upstream remote repository |
| `git remote rm upstream` | Remove upstream remote |