﻿# Git Basics: Commands, Concepts, and Best Practices

## Initializing a Git Repository

```sh
git init
```
- Initializes a new Git repository.
- Creates a `.git/` directory that stores Git’s internal data structure.
- To verify, run:
  ```sh
  ls -a
  ```
  This will list all files, including the hidden `.git/` directory.

## Understanding the `.git/` Directory

Opening `.git/` reveals various internal structures:
- `branches/`, `HEAD`, `config`, `info/`, `objects/`, `refs/`, `hooks/`, etc.
- These are **implementation details**; modifying them directly may corrupt your repository.

---

## Basic Git Workflow

### Staging and Committing Changes
A **commit** is a snapshot of your project at a point in time.
Git uses a **staging area** (also called the **index**) to allow you to selectively commit changes.

```sh
git add file1 file2  # Adds specific files
git add .            # Adds all changes recursively
git commit -m "Meaningful commit message"
```
- Running `git commit` without `-m` opens your default text editor for writing a commit message.
- Follow this structure:
  ```
  Short description (one line)
  
  Detailed explanation of changes, if necessary.
  ```
- Each commit has a **SHA-256 hash ID**, timestamp, author details, and a snapshot of the project.

### Best Practices for Commits
✅ **Commit often**, whenever you implement a unit of work.
✅ Ensure commits are **self-contained, independent, and logically separated**.
✅ **Avoid:**
   - Committing very small changes (single file change unless necessary).
   - Large, multi-purpose commits that mix unrelated changes.
✅ Use **simple past or present tense** in commit messages (depending on team guidelines).

```sh
git commit -am "Commit message"  # Skips explicit staging (only for modified files, not new ones)
```

---

## Staging Area Management

### Listing Staged Files
```sh
git ls-files  # Shows files in the staging area
```

### Ignoring Files
Certain files should not be tracked, such as:
- Logs, temporary files, cached data, build artifacts.
- Specify these in `.gitignore`.
- Example `.gitignore` for Python:
  ```
  __pycache__/
  *.log
  *.tmp
  ````
- Standard templates available on GitHub for various languages.

### Removing Files
```sh
git rm file_name     # Removes from working directory and staging area
git rm --cached file # Removes only from staging area, keeps in working directory
```

---

## Checking Repository Status

### Short Status View
```sh
git status -s
```
- **Left column**: Staging area.
- **Right column**: Working directory.
- Example output:
  ```
  M  file1.txt   # Modified in staging area
   M file2.txt   # Modified in working directory
  ?? newfile.txt # Untracked file
  ```

---

## Viewing Changes

### Checking Differences
```sh
git diff            # Working directory vs. staging area
git diff --staged  # Staged area vs. last commit
```

### Visual Diff Tools
Configure a visual diff tool like VS Code or WinMerge:
```sh
git config --global diff.tool vscode
```
Use it with:
```sh
git difftool       # View differences visually
git difftool --staged
```

---

## Viewing Commit History
```sh
git log            # Full history (press 'q' to quit, space to scroll)
git log --oneline  # Concise view
git log --graph    # Visual representation
git log --reverse  # Show commits in reverse order
```

### Viewing a Specific Commit
```sh
git show <commit_hash>  # View commit details
git show HEAD           # View last commit
git show HEAD~1         # View commit before the last one
git show HEAD~1:file.ext # View a specific file from a previous commit
```

### Understanding Git’s Storage
```sh
git ls-tree HEAD  # Lists files in the current commit
```
- Each file is stored as a **blob**, and directories are stored as **trees**.

---

## Undoing Changes

### Unstaging Files
```sh
git restore --staged file_name   # Removes file from staging but keeps changes
```

### Discarding Local Changes
```sh
git restore file_name            # Restores from the staging area
git restore --source=HEAD~1 file # Restores to the previous commit’s version
```

### Cleaning Untracked Files
```sh
git clean -fd  # Removes all untracked files and directories
```

---

## Summary of Common Commands

| Command | Description |
|---------|-------------|
| `git init` | Initialize a Git repository |
| `git add <file>` | Stage changes |
| `git commit -m "message"` | Commit changes with a message |
| `git status` | Show working and staging area status |
| `git diff` | Show changes between working directory and staging area |
| `git diff --staged` | Show changes between staging area and last commit |
| `git log --oneline` | Show commit history in a compact format |
| `git rm <file>` | Remove a file from the repository |
| `git restore --staged <file>` | Unstage a file without losing changes |
| `git clean -fd` | Remove untracked files |
