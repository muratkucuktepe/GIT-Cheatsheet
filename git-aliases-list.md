### GIT ALIASES
**0 - Display list of global aliases**
```
git config --global --list
```
---

**1 - Find a file path in codebase**
```
f = "!git ls-files | grep -i"
Usage: git f <myFile>
```
---
**2 - Show which file is changed in each commit**
```
ll = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
Usage: git ll
```
---
**3 - Show commit history in a formatted way**
```
Global Config File:
hist = log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short
Command line: git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
Usage: git ll
```
---
