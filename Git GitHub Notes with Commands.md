___
## 1️⃣ **Git Basics**
### 🔹 Install Git
Git is a version control system that helps track changes in source code during software development. It is used to coordinate work among multiple developers and maintain a history of changes.
- **Download Git** from the official website: [https://git-scm.com/downloads](https://git-scm.com/downloads)
- **Check if Git is installed** using the following command:
  ```bash
  git --version
  ```

### 🔹 Configure Git (Set Identity)
Before making any commits, configure your Git identity so that your contributions are correctly attributed.
```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

### 🔹 Initialize a Repository (Start Tracking)
To start tracking a project with Git, initialize a repository inside the project folder.
```bash
git init
```
This command creates a hidden `.git` directory that stores all version control information.

---
## 2️⃣ **Working with Repositories**
### 🔹 Clone an Existing Repository
To work on a project that is already hosted on GitHub, clone it to your local machine.
```bash
git clone https://github.com/username/repository.git
```
This command downloads all files and history from the repository.

### 🔹 Check Repository Status
The `git status` command shows the current state of the working directory and staging area.
```bash
git status
```
It helps track new, modified, or deleted files that haven't been committed yet.

### 🔹 Add Files to Staging
Before committing changes, files must be added to the staging area.
```bash
git add filename     # Add a specific file
git add .            # Add all modified files
```
This prepares files for committing.

### 🔹 Commit Changes
A commit saves the changes permanently in the version history.
```bash
git commit -m "Your commit message"
```
A good commit message should be clear and concise, describing the changes made.

### 🔹 View Commit History
To see a list of past commits:
```bash
git log              # Detailed commit history
git log --oneline    # Shorter commit messages
```
This helps track changes over time.

---
## 3️⃣ **Branching & Merging**
Branches allow multiple developers to work on different features simultaneously without affecting the main codebase.

### 🔹 Create a New Branch
```bash
git branch branch-name
```
A branch is a separate version of the project where new changes can be tested.

### 🔹 Switch to a Branch
```bash
git checkout branch-name  # Older method
git switch branch-name    # Newer method
```
This moves the working directory to the specified branch.

### 🔹 Create & Switch to a New Branch
```bash
git checkout -b new-branch
```
This command creates a new branch and switches to it.

### 🔹 Merge a Branch
```bash
git checkout main         # Switch to main branch
git merge branch-name     # Merge changes from another branch
```
Merging integrates changes from one branch into another.

### 🔹 Delete a Branch
```bash
git branch -d branch-name     # Delete local branch
git push origin --delete branch-name  # Delete remote branch
```
Cleaning up unused branches keeps the repository organized.

---
## 4️⃣ **Pushing & Pulling to/from GitHub**
### 🔹 Add Remote Repository
Connect your local repository to a remote repository hosted on GitHub.
```bash
git remote add origin https://github.com/username/repository.git
```

### 🔹 Push Code to GitHub
```bash
git push origin branch-name
```
Uploads local commits to the remote repository.

### 🔹 Pull Latest Changes from Remote
```bash
git pull origin branch-name
```
Downloads and integrates changes from the remote repository.

### 🔹 Set Default Branch for Pushing
```bash
git push -u origin main
```
This makes `main` the default branch for future pushes.

---
## 5️⃣ **Undoing Changes**
Mistakes happen! Git allows you to undo changes in different ways.

### 🔹 Undo Changes Before Staging
```bash
git checkout -- filename   # Revert changes in a file
```
This discards modifications in the working directory.

### 🔹 Unstage a File (Keep Changes)
```bash
git reset filename
```
This removes a file from staging but keeps the changes in the working directory.

### 🔹 Undo Last Commit (Keep Changes)
```bash
git reset --soft HEAD~1
```
This resets the last commit but keeps changes staged.

### 🔹 Undo Last Commit (Discard Changes)
```bash
git reset --hard HEAD~1
```
This removes the last commit and discards all changes.

---
## 6️⃣ **GitHub Authentication (Personal Access Token)**
GitHub no longer supports password authentication. Instead, use a **Personal Access Token (PAT)**.
```bash
git push https://github.com/username/repository.git
```
When prompted, enter your **Personal Access Token (PAT)** instead of a password.

---
## 7️⃣ **Stashing (Temporary Changes Storage)**
If you need to switch branches but have uncommitted changes, stash them temporarily.

### 🔹 Save Uncommitted Changes
```bash
git stash
```
### 🔹 Apply Stashed Changes
```bash
git stash pop
```
### 🔹 View Stashed Changes
```bash
git stash list
```

---
## 8️⃣ **Tagging Versions**
Tags mark specific commits as important releases.

### 🔹 Create a Tag
```bash
git tag v1.0
```
### 🔹 Push Tags to Remote Repository
```bash
git push origin --tags
```

---
## 9️⃣ **Git Ignore**
### 🔹 Ignore Files & Folders
Use `.gitignore` to exclude files from version control.
```
node_modules/
*.log
.env
```

---
## 🔟 **Reset & Revert**
### 🔹 Revert a Specific Commit (Create New Commit to Undo Changes)
```bash
git revert commit-hash
```
### 🔹 Reset to a Specific Commit (Discard Changes After It)
```bash
git reset --hard commit-hash
```

---
## 🎯 **Summary of Essential Commands**
```bash
git init                       # Initialize a repository
git clone <repo-url>           # Clone a repository
git status                     # Check repository status
git add .                      # Stage all changes
git commit -m "message"        # Commit changes
git branch branch-name         # Create a new branch
git checkout branch-name       # Switch branches
git merge branch-name          # Merge a branch
git push origin branch-name    # Push code to GitHub
git pull origin branch-name    # Pull latest changes
git log --oneline              # View commit history
```


