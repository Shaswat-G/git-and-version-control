# Git Branching, Merging & Rebasing

## Branching Basics
Branching allows you to separate from the main line of work and develop features in isolation.

- **`master` (main workspace)** → Stable version of the code.
- **`feature-branch` (isolated workspace)** → Work on new developments.
- Once the feature is complete, merge it back into `master`.
- **`master` is a pointer** to the latest commit in the main line of work.

### Creating and Switching Branches
```sh
git switch -c <branch_name>  # Create and switch to a new branch
git branch                   # List all branches
git branch -m old_name new_name  # Rename a branch
git branch -d <branch_name>   # Delete a branch
```

### Comparing Branches
```sh
git log master..<branch_name>  # Shows commits in branch but not in master
git diff master..<branch_name>  # Shows file changes (--name-only, --name-status)
```

## Stashing Changes
Stashing allows you to temporarily save changes before switching branches.

```sh
git stash push -m "Meaningful message"  # Save changes with a label
git stash list                          # List all stashes
git stash show <index>                   # View a specific stash
git stash drop <index>                   # Remove a specific stash
git stash clear                          # Remove all stashes
```
- By default, untracked files are **not** stashed. Use `--all` to include them.

## Merging Branches
### Merge Types
1. **Fast-forward Merge** → Moves `master` pointer forward if no new commits exist in `master`.
2. **Three-way Merge** → Used when branches diverged, creating a merge commit.

```sh
git switch master
git merge <branch_name>
```

### Handling Merge Conflicts
- Manually resolve conflicts in files.
- Use graphical tools for easier conflict resolution (e.g., P4Merge, Kdiff3).

```sh
git config --global merge.tool p4merge
git mergetool  # Launches the merge tool
```

### Undoing a Merge
```sh
git merge --abort   # Cancels an in-progress merge
git reset --hard HEAD~1  # Reverts to the last commit before merging
```
If already pushed:
```sh
git revert -m 1 HEAD  # Reverts a merge commit
```

## Squash Merging
Squash merging combines multiple commits into a **single** commit before merging.
```sh
git switch master
git merge --squash <branch_name>
git commit -m "Merged feature branch"
git branch -D <branch_name>  # Delete branch after squash merge
```

## Rebasing (Rewriting History)
Rebasing moves a branch’s starting point to the latest commit in `master`, keeping history linear.
```sh
git switch <branch_name>
git rebase master  # Moves branch to latest master commit
```
**Handling conflicts during rebase:**
```sh
git rebase --continue  # After resolving conflicts
git rebase --abort     # Cancel rebase
```
⚠️ **Do not rebase after pushing commits to a shared repository.**

## Cherry-picking
Pick a specific commit from another branch and apply it to the current branch.
```sh
git cherry-pick <commit_hash>
```

## Restoring a File from Another Branch
```sh
git restore --source=<branch_name> -- <filename>
```

## Summary of Key Commands

| Command | Description |
|---------|-------------|
| `git switch -c <branch>` | Create and switch to a branch |
| `git branch -d <branch>` | Delete a branch |
| `git log master..<branch>` | Show commits in a branch but not in master |
| `git diff master..<branch>` | Show file changes between branches |
| `git stash push -m "msg"` | Stash changes temporarily |
| `git merge <branch>` | Merge a branch into the current branch |
| `git merge --squash <branch>` | Squash merge a branch |
| `git rebase master` | Rebase a branch onto master |
| `git cherry-pick <commit>` | Apply a specific commit to the current branch |

I have clearly lost respect. I think its better to not discuss it and let it go and let her have some space.