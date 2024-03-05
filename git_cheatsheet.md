### INITIALIZE GIT
---

**- Initialize git which creates .git folder**
```
git init
```
### CLONE
---

**- Clone a repo from a url**
```
git clone <url>   // Be sure that you are not already in a repo
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
**- Switch a remote branch which has just a reference locally.**
```
git switch <remote-branch>                      // 1. way (new way) Ex: git switch my-remote-branch
git checkout --track <remote>/<remote-branch>   // 2. way (old way) Ex: git checkout --track origin/my-remote-branch
```

### CLEAN UP BRANCH

**- Update local list of remote branches.**
```
git remote update origin --prune
```

### DELETE BRANCH

**- Delete branch (2 ways). It only deletes the branch if it has already been fully merged in its upstream branch. You can not delete branch you are on.**
```
git branch -d <branch-name-to-delete>         // 1. way
git branch --delete <branch-name-to-delete>   // 2. way
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
git stash        // 1. Way
git stash save   // 2. Way
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
### WORKING WITH PREVIOUS COMMITS / BRANCHES

**- Switching a certain commit at the branch history**
```
// The first 7 digits of the long hash can be also used here.
git checkout <commit-hash>   // It gives a DETACHED HEAD error because HEAD points to a hash insead of branch reference.
```
**- Switching previously checked out branch**
```
git checkout -
```
**- Switching X commit before master**
```
git checkout HEAD~X   // Ctrl + Alt + + -> ~ on keyboard
```
**- Undoing the the last changes to the last commit. ROLLBACK -> It goes back to recent commit, deletes recent unsaved changes**
```
git checkout HEAD <file-name>                 // 1. Way
git checkout -- <file-name>                   // 2. Way
git restore <file-name>                       // 3. Way
git checkout -- <file-name-1> <file-name-2>   // With multiple files
```
**- Restoring to X commits before HEAD**
```
// Can not retrieve last unsaved changes.
// But you can use git restore <file-name> to restore till to HEAD
git restore --source HEAD~X <file-name>    // It is possible to restore multiple files like above
```
**- Restoring what you accidentally added to the staging area with git add and need to unstage them**
```
git restore --staged <file-name>
```
**- RESET: Undoing commits WITHOUT losing changes in working directory**
```
// If you committed accidentally, firstly check the log
git log --oneline
// Then copy NOT the LAST but PREVIOUS following commit hash.
// If you have commits first-second-third and you want to remove third, choose second commits hash.
git reset <commit-hash>  // This DOESN'T delete the changes in your WORKING DIRECTORY
```
**- RESET HARD: Undoing commits BY also losing changes in working directory**
```
// If you committed accidentally, firstly check the log
git log --oneline
// Then copy NOT the LAST but PREVIOUS following commit hash.
// If you have commits first-second-third and you want to remove third, choose second commits hash.
git reset --hard <commit-hash>  // This DELETES the changes in your WORKING DIRECTORY
```
**- REVERT: Removing commit by creating an extra new commit and deleting changes in working directory**
```
// If you committed accidentally, firstly check the log
git log --oneline
// Then copy the LAST commit
git revert <commit-hash>  // This DELETES the changes in your WORKING DIRECTORY
// This will generate a NEW commit, ahead of the old ones and reverts the changes.
// But then a new screen appears. You should write commit message because git revert creates a new commit.
// IMPORTANT: This deletes the changes in the reverted commit.
// If other collaborators have the copy of the commit which you want to revert, do not use reset but use revert.
// It will create new commit, so collaborators can deal with it.
```

### REMOTES

**- Displaying a list of remotes**
```
git remote   // Remotes
git remove -v    // Verbose, for more info
```
**- Adding a new remote**
```
git remote add <name> <url>   //Ex: git remote add origin https://github.com/blah/repo.git
```
**- Renaming a remote**
```
git remote rename <old> <new>   // Rename it
git remote remove <name>        // Remove old one
```

### PUSH

**- Pushing local branch A to remote branch A (if there  is no remote branch, it creates new)**
```
// Pushing local master branch to remote
// You do not need to be on the same branch. You can be on branch A and use command git push origin branch-B
git push <remote> <branch>   // Common pattern: git push origin master 
```
**- Pushing local branch A to remote B**
```
// Pushing local master branch to remote
git push <remote> <local-branch>:<remote-branch>  // Common pattern: git push origin master

// Ex: Pushing local branch called apple to remote branch banana in remote origin
git push origin apple:banane
```
**- Connecting local branch A with remote branch A**
```
// Connect the local branch A to remote branch B. -u stands for upstream
git push -u <remote> <remote-branch>            // 1. Way Ex: git push -u origin master
git push --set-upstream origin <remote-branch>   // 2. Way

// If you do it once, you can use shorthand afterwards.
git push

// If you want to set upstream branch which is different than local branch
git push -u <remote> <local-branch>:<remote-branch>

// Ex: Connecting local branch called apple to remote branch banana in remote origin
git push -u origin apple:banana
```
### TRACKING BRANCHES
---
**- View the remote branches our local repository knows about.**
```
git branch -r
```
### FETCHING UPDATES
---
**- Fetch everything from origin**
```
// It fetches new code from remote to the local repository, NOT working directory
git fetch <remote>   // If not specified, remote defaults to origin
```
