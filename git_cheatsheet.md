### INITIALIZE GIT
---

**- Initialize git which creates .git folder**
```
git init
```

### ADD & COMMIT
---
**- Adding all changes in working directory to the stage area.**
```
git add .
```

---
**- Adding multiple changes from working directory to the staging area (first-file, second-file).**
```
git add <first-file> <second-file>`
```

---
**- Commiting a change with message.**
```
1: git add .                           // Add changes to the staging area
2: git commit -m "your-message-here"   // Commit with a message
```
---
**- Adding a change to staging area and commiting at the same time**
```
git commit -a -m "your-message-here"   // 1. Way
git commit -am "your-message-here"     // 2. Way
```

### AMEND
---

**- Amend the last commit.**
```
git add <my-forgotten-changes>   // Stage your forgotten changes
git commit --amend               // Amend your last commit
                                 // Write your commit on terminal and hit esc, then wq!
```

### CONFIGURATION
---

**- Change username.**
```
git config user.name "your-user-name"
```
**- Show username.**
```
git config user.name
```
**- Set to update the local list of remote git branches automatically every time you run git pull or git fetch using below command.**
```
git config remote.origin.prune true
```

### CREATE BRANCH

**- Create a new branch from current branch and switch to that branch.**
```
git branch <new-branch-name>   // Create branch
git switch <new-branch-name>   // Switch to the new branch
```
**- Create a new branch from current branch and switch to that branch directly.**
```
git switch -c <new-branch-name-to-create>     // 1. way
git checkout -b <new-branch-name-to-create>   // 2. way
```

### SHOW BRANCH

**- Show current branch.**
```
git branch
```

### SWITCH BRANCH

**- Switch branch.**
```
git switch <branch-name-to-switch>     // 1. way
git checkout <branch-name-to-switch>   // 2. way
```

### CLEAN UP BRANCH

**- Update local list of remote branches.**
```
git remote update origin --prune
```

### DELETE BRANCH

**- Delete branch (2 ways). It only deletes the branch if it has already been fully merged in its upstream branch. You can not delete branch you are on.**
```
git branch -d <branch-name-to-delete>         // 2. way
git branch --delete <branch-name-to-delete>   // 1. way
```
**- Delete branch. It deletes the branch irrespective of its merged status. This is a short version of '*"git branch --delete --force <branch-name-to-delete>". You can not delete branch you are on.***
```
git branch -D <branch-name-to-delete>
```
**- Delete remote branch.**
```
git push -d origin <branch-name-to-delete>
```

### RENAME BRANCH

**- Rename your local branch. You should be on the branch in order to rename it.**
```
git branch -m <new-branch-name>
```

### LOGS

**- Show the commit logs.**
```
git log
```
**- Show the commit logs in oneline.**
```
git log --oneline
```

### MERGE BRANCH

**- Merging branch A into branch B**
```
git switch <branch-B>   // Switch branch.
git merge <branch-A>    // Merge branch A into B
```

### DIFF

**- List all the changes in the working directory that are NOT STAGED for the next commit.**
```
git diff
```
**- List all the changes in the working tree since your last commit.(STAGED and UNSTAGED changes)**
```
git diff HEAD
```
**- List all the changes in the working tree of a SPECIFIC FILE since your last commit.(STAGED and UNSTAGED changes)**
```
git diff HEAD <file-name>
```
**- List all the changes between staging area and your last commit. (STAGED CHANGES)**
** "Show me what will be included in my commit if I run git commit right now**
```
git diff --staged   // 1. Way
git diff --cached   // 2. Way
```
**- List all the changes between staging area and your last commit of a SPECIFIC FILE. (STAGED CHANGES)**
```
git diff --staged <file-name>
```
**- List all the changes between two BRANCHES BranchA and BranchB. Place of the files matters, AB or BA**
```
git diff BranchA..BranchB   // 1. Way
git diff BranchA  BranchB   // 2. Way
```
**- List all the changes between two COMMITS CommitHashA and CommitHashB. Place of the files matters, AB or BA**
```
git diff CommitHashA..CommitHashB   // 1. Way
git diff CommitHashA  CommitHashB   // 2. Way
```
### STASH CHANGES

**- Stashing (or saving) your changes**
```
git stash
```
**- Re-applying stashed changes. It removes saved changes from stash**
```
git stash pop
```
**- Re-applying stashed changes without removing stash. This is useful if stash is applied multiple branches**
```
git stash apply
```
**- Stashing multiple times**
```
// Make first change
git stash                   // 1st stash
// Make second change
git stash                   // 2nd stash
// Make third change
git stash                   // 3rd stash
git stash list              // show the list of stashes
git stash apply stash@{2}   // Applying just a specific stash, second stash, but does not remove stash
git stash drop stash@{2}    // Removes the second stash
git stash clear             // Clears all stash
```
