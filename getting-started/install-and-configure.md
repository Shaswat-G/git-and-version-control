## Installing Git
- Download from [git-scm.com/downloads](https://git-scm.com/downloads).
- Verify installation:
  ```sh
  git --version
  ```

---

## Configuring Git
Git requires initial setup for user identity, editor preferences, and line endings.

### **1. User Identity**
```sh
git config --global user.name "your_name"
git config --global user.email "your_email@email.com"
```

### **2. Default Editor (Use VS Code)**
```sh
git config --global core.editor "code --wait"
```
- The `--wait` flag ensures the terminal waits until VS Code is closed.

### **3. Editing Git Configuration**
```sh
git config --global -e
```
(This opens Git's global config in VS Code.)

### **4. Diff Visual Editor (Use VS Code)**
```sh
git config --global diff.tool vscode
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
```

### **4. Graphical Merge tool (Use p4merge)**
```sh
git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "C:\program_files\full_path_to_p4_merge"
```

---

## Managing Line Endings (EOL)
Different OS handle end-of-line (EOL) characters differently:
- **Windows:** Uses `\r\n` (Carriage Return + Line Feed)
- **Mac/Linux:** Uses `\n` (Line Feed only)

To handle this automatically:
```sh
git config --global core.autocrlf true   # Windows users
git config --global core.autocrlf input  # Mac/Linux users
```

---