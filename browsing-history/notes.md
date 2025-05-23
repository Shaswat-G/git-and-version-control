# Advanced Git Commands & Concepts

## Searching for Commits

### By Author, Date, Email, or Message
```sh
git log --oneline --stat --graph --reverse  # Full structured log
```
- `git log --oneline -3` → Last 3 commits
- `git log --author="Name"` → Commits by a specific author
- `git log --before="date" --after="date"` → Filter by time range
- `git log --grep="search term"` → Search commit messages (case-sensitive)
- `git log -S"function_name()"` → Commits that added or removed a specific line

### Searching Within a Range
```sh
git log --oneline <commit1>..<commit2>  # View commits between two commits
```
- `git log --oneline <filename>` → View commits related to a file
- `git log --patch` → View exact changes
- `git log --pretty=format:"<custom format>"` → Fully customizable output

## Creating Git Aliases
Define custom commands for convenience:
```sh
git config --global alias.lg "log --oneline --graph"
git config --global alias.unstage "restore --staged ."
```
Usage:
```sh
git lg  # Runs the custom log command
git unstage  # Restores all staged files
```

## Viewing Commits
- `git show <commit>` → View commit details
- `git show HEAD~3` → View 3 commits before HEAD
- `git show HEAD~3:<file_path>` → View a specific file from that commit
- `git show --name-only` → Show only file names modified in the commit
- `git show --name-status` → Show file names with their modification type

## Comparing Commits
```sh
git difftool HEAD~4 HEAD~1  # Compare two commits
```
- Add `:<file_path>` to limit to a specific file
- `--name-only` → Shows only file names
- `--name-status` → Shows file names with their modification type

## Understanding HEAD & Detached HEAD State
- `git checkout <commit>` → Enters **detached HEAD state** (temporary checkout)
- **Detached HEAD commits** are not part of any branch and can be garbage collected.
- `git log` will show commits only up to HEAD, not the full history to `master`.

## Finding Bugs with Git Bisect (Binary Search for Bugs)
```sh
git bisect start
git bisect bad  # Marks current commit as faulty
git bisect good <commit_id>  # Marks a known good commit
```
Git will checkout a middle commit:
- If the commit is good: `git bisect good`
- If the commit is bad: `git bisect bad`
- Repeat until the problematic commit is found.
- `git bisect reset` → Exit bisect mode and return to `master`.

## Finding the Most Active Contributors
```sh
git shortlog -nse --before="YYYY-MM-DD" --after="YYYY-MM-DD"
```
- Shows commit count and email of each contributor.

## Viewing File History
```sh
git log --oneline --stat <file>
```
- `git log --patch <file>` → Show exact changes.

## Restoring a Deleted File
If a file was deleted in a previous commit:
```sh
git checkout HEAD~1 -- <file_name>
git commit -m "Restored <file_name>"
```

## Blaming: Finding Who Changed a Line
```sh
git blame -L 20,50 <file>
```
- Shows who modified lines **20 to 50**.

## Tagging Commits
- `git tag v1.0 <commit>` → Tag a specific commit.
- `git tag` → List all tags.
- `git show <tag>` → View the tagged commit.
- `git checkout <tag>` → Checkout a tag.
- `git tag -d <tag>` → Delete a tag.

## Summary of Key Commands

| Command | Description |
|---------|-------------|
| `git log --oneline` | View commit history in a compact format |
| `git log --grep="term"` | Search commit messages |
| `git log -S"code"` | Find commits adding/removing specific code |
| `git show HEAD~2` | Show details of an older commit |
| `git diff HEAD~2 HEAD` | Show differences between commits |
| `git checkout <commit>` | Checkout an older commit (detached HEAD) |
| `git bisect start` | Start debugging commits using binary search |
| `git shortlog -nse` | Show contributors ranked by commit count |
| `git blame <file>` | Show who last modified each line |
| `git tag v1.0` | Tag the latest commit as `v1.0` |