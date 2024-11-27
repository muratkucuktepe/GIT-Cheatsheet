### INITIALIZE GIT

**- Initialize git which creates .git folder**
```
git init
```
---
### CLONE
**- Clone a repo from a url**
```
git clone <url>   // Be sure that you are not already in a repo
```
---
### UPDATE
**- Update git**
```
git update
```
---
### ADD & COMMIT
**- Adding all changes in working directory to the stage area.**
```
git add .
```
**- Adding multiple changes from working directory to the staging area (first-file, second-file).**
```
git add <first-file> <second-file>`
```
**- Commiting a change with message.**
```
1: git add .                           // Add changes to the staging area
2: git commit -m "your-message-here"   // Commit with a message
```
**- Adding a change to staging area and commiting at the same time**
```
git commit -a -m "your-message-here"   // 1. Way
git commit -am "your-message-here"     // 2. Way
```
---
### AMEND
**- Amend the last commit.**
```
git add <my-forgotten-changes>   // Stage your forgotten changes
git commit --amend               // Amend your last commit
                                 // Write your commit on terminal and hit esc, then wq!
```
---
### CONFIGURATION
```
// Local config file is under ./git config
// Local config file is valid for ONE repo
// Global config file is under either ~/.config or ~/.config/git/config
// Global config file is for ALL repos
```
**- Change username or e-mail address.**
```
git config user.name "your-user-name"              // Change locally. If you do not specify, default is local
git config --local user.name "your-user-name"      // Change locally
git config --global user.name "your-user-name"     // Change globally
git config --global user.email "your-user-email"   // Change globally 
```
**- Show username.**
```
git config user.name
```
**- Set to update the local list of remote git branches automatically every time you run git pull or git fetch using below command.**
```
git config remote.origin.prune true
```
**- Listing global configs and editing them (Ex: alias).**
```
// Get the list with keys
git config --global --list 
// Remove a config with key example
git config --global --unset alias.myCustomAlias
// Edit config file directly with command line
git config --global --edit
```
---
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
---
### SHOW BRANCH
**- Show current branch.**
```
git branch
```
---
### CHERRY PICK
**- Cherry picking**
```
git cherry-pick <commit-hash>
```
---
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
---
### CLEAN UP BRANCH
**- Update local list of remote branches.**
```
git remote update origin --prune
```
---
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
---
### RENAME BRANCH
**- Rename your local branch. You should be on the branch in order to rename it.**
```
git branch -m <new-branch-name>
```
---
### LOGS
**- Show the commit logs.**
```
git log
```
**- Show the commit logs in oneline.**
```
git log --oneline
```
---
### MERGE BRANCH
**- Merging branch A into branch B**
```
git switch <branch-B>   // Switch branch.
git merge <branch-A>    // Merge branch A into B
```
---
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
**- Time based diffs**
```
// Examples
git diff HEAD HEAD@{yesterday}
git diff master master@{yesterday}
```
---
### STASH CHANGES
**- Stashing (or saving) your changes**
```
git stash        // 1. Way
git stash save   // 2. Way
```
**- Stashing with a message**
```
git stash push -m "your-message"
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
---
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

// Reverting the last PR
git commit -m 1 <pr-commit-hash>
```
---
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
---
### PUSH
**- Pushing local branch A to remote branch A (if there  is no remote branch, it creates new)**
```
// git push does not push tags.
// Pushing local master branch to remote
// You do not need to be on the same branch. You can be on branch A and use command git push origin branch-B
git push <remote> <branch>   // Common pattern: git push origin master 
```
**- Pushing local branch A to remote B**
```
// Pushing local master branch to remote
git push <remote> <local-branch>:<remote-branch>

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
---
### PULL
**- Pulling changes integrates remote changes to local changes which you are currently on.**
```
// git pull = git fetch + git merge
git pull <remote> <remote-branch>   // Ex: git pull origin master
git pull  // Shorter syntax. If remote is default to origin and remote branch will be default to your configured branch.
```
---
### TRACKING BRANCHES
**- View the remote branches our local repository knows about.**
```
git branch -r   // Note: It shows just remote branches in LOCAL REPOSITORY not in Origin!
```
---
### FETCHING UPDATES
**- Fetch everything from origin**
```
// It fetches new code from remote to the local repository, NOT working directory
git fetch <remote>   // If not specified, remote defaults to origin
git fetch            // You can just shorten it. After that git status shows your difference with remote
```
```
git fetch <remote> <branch>      // Fetches from a specific branch. Ex: git fetch origin master
git checkout <remote>/<branch>   // To see the fetched changes. Ex: git checkout origin/master   
```
---
### REBASE
**- Rebasing feature branch on top of master branch.**
```
git switch feature   // Switch to the feature branch
git rebase master    // Put it on top of master branch Ex: M + M + M + F + F
```
**- Abort rebasing in case of a conflict.**
```
git rebase --abort
```
**- Solving merge conflicts after rebase**
```
// After you rebase and solve merge conflicts
git add <files>
git rebase --continue
```
**- Interactive rebase**
```
// -i means interactive mode
git rebase -i HEAD~4   // Rebase not another branch but some commits on to the head they are currently on.

// Text editor will be opened.
pick:   use the commit
reword: use the commit but edit the commit message
edit:   use commit but stop for amending
fixup:  use commit contents but meld it into previous commit and discard the commit message
drop:   remove commit
```
---
### TAGS
**- Listing and searching for tags**
```
git tag               // Lists all tags
git tag -l "*WORD*"   // Searches WORD in tags with wildcard. -l means list
```
**- Check out different tags**
```
git checkout <tag>  // Ex: git checkout 17.1.1
```
**- Find the difference between two tags.**
```
git diff <tag1> <tag2>   // Ex: git diff v5.1.1 v5.1.0
```
**- Adding lightweight tag.**
```
git tag <tagname>   // git tag v5.1.1
```
**- Adding annotated tag.**
```
git tag -a <tagname>   // Ex: git tag -a v5.1.1
// To display the tagger, date etc. use
git show <tagname>   // Ex: git tag v5.1.1
```
**- Tagging previous commit with hash number**
```
git tag <tagname> <commmit-hash>   // Ex: git tag v5.1.2 56e85468
```
**- Moving an already existing tag to another commit**
```
// Each tag is unique. If you want to take existing tag and move to another commit use:
// -f means force
git tag <tagname> <new-commmit-hash> -f   // Ex: git tag v5.1.2 56e85468 -f 
```
**- Deleting tags**
```
git tag -d <tagname>   // -d means delete
```
**- Pushing tags**
```
// Pushing a single tag to remote
git push <remote> <tagname>   // Ex: git push origin v1.2.2

// Pushing all the tags at once
git push <remote> --tags   // Ex: git push origin --tags
```
---
### CONFIG FILE
**- Editing config file under .git directory**
```
[color]                    
    ui = true
[color "branch"]            // Branch color settings
    local = cyan            // Setting local branch color
    current = yellow blink  // Setting current branch color 
[color "diff"]
    old = magenta bold      // Setting outcome of diff
```
### HASHING
**- Hashing a word or a file**
```
// A blob is a file
// A tree is a directory
// A tree can have blobs and trees in it.

echo 'a-word' | git hash-object --stdin     // Returns a 40-char long hash but does not store in git database. This is just echo
echo 'a-word' | git hash-object --stdin -w  // Returns hash and stores it in .git. w means write.
// It stores with first 2 chars as a folder, and the rest 38 chars as file. It is saved as encrypted binary, not readable.

git hash-object aFile.txt                   // Hashing a text file without storing
git hash-object aFile.txt -w                // Hashing a text file and storing it
git cat-file -p <object-hash> > aFile.txt   // Retrieves values from hash and stores them in aFile.txt
```
**- Retrieving hashed data back from git database**
```
git cat-file -p <object-hash>   // This prints the human readable value of the stored hash. p means print
// 40-char hash value as well as shortened version (5-chars) can be used.
```
**- Viewing a tree and the type of the hash**
```
git cat-file -p master^{tree}   // Views master branch tree
git cat-file -t <object-hash>   // Shows the type of the hash object. t means type
```
---
### REFLOGS
**- Reflogs file in .git directory.**
```
// Git keeps reflogs just on your activity.
// Git cleans them after 90 days. It is configurable
```
```
// There are other qualifiers as well. expire, delete, exists
git reflog show HEAD            // Shows the logs of HEAD
git reflog show <branch-name>   // Shows the logs of a specific branch
git reflog                      // Shows the log of a specific reference. Default is HEAD
```
**- Going back to a certain reflog**
```
// name@{qualifier} is used.
git reflog show HEAD${2}   // Shows 2 steps before
```
```
// There is a difference between HEAD~2 and HEAD@{2}
// HEAD~2 shows 2 commits ago
// HEAD@{2} shows 2 steps back at reflogs
```
**- Time based reflogs**
```
// Examples
git reflog master@{one.week.ago}
git checkout bugfix@{2.days.ago}
git checkout bugfix@{two.days.ago}
git reflog master@{one.month.ago}
git diff main@{0} main@{yesterday}
```
**- Rescuing hard reset commits with reflogs**
```
// If you reset hard the last commit by using git reset --hard <one-previous-commit-hash>
git reflog show master        // Show the reflogs on current branch. In this case master.
git reset --hard master@{1}   // Bring back the commit either using qualifier or hash. In this case qualifier.
```
---
### ALIASES
**- Setting aliases for commands.**
```
// Find the global file: ~/.config or ~/.config/git/config
// Set s for git status and l for git log
[alias]
   s=status
   l=log
```
```
// Adding alias from command line
// Set git displaybranches as alias for git branch
git config --global alias.displaybranches branch
```
**- Setting aliases with arguments**
```
[alias]
   cm=commit -m
   a=add file1 file2

// Now you can use
git cm "My commit message without -m"
git a firstFile secondFile
```
```
// Useful links
https://www.durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/
https://github.com/GitAlias/gitalias
https://gist.github.com/mwhite/6887990
```
### SUBMODULES

**- Initialize git which creates .git folder**
```
git submodule add <github-link>  // This creates a .gitmodules file for submodules.
git add .
git commit -m "Your-message"
```
