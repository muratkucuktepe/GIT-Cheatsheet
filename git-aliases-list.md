### GIT ALIASES
**0 - Display list of global aliases**
```
// Get the list with keys
git config --global --list 
// Remove a config with key example
git config --global --unset alias.myCustomAlias
// Edit config file directly with command line
git config --global --edit
```
---

**1 - Find a file path in codebase**
```
Global Config File:
f = "!git ls-files | grep -i"
Command line: git config --global alias.f '!git ls-files | grep -i'
Usage: git f <myFile>
```
---
**2 - Show which file is changed in each commit**
```
Global Config File:
ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
Command line: git config --global alias.ll "log --pretty=format:'%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]' --decorate --numstat"
Usage: git ll
```
---
**3 - Show commit history in a formatted way**
```
Global Config File:
hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
Command line: git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
Usage: git hist
```
---
**4 - Show last commit**
```
Global Config File:
last = log -1 HEAD
Command line: git config --global alias.last "log -1 HEAD"
Usage: git last
```
---
**5 - List of commits which are not pushed to remote yet**
```
Global Config File:
unpushed = '!git log --oneline --all --not --remotes=origin'
Command line: git config --global alias.unpushed '!git log --oneline --all --not --remotes=origin'
Usage: git unpushed
```
