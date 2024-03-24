### GIT ALIASES

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
