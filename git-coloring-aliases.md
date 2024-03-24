### Coloring Aliases
```
// Available colors: normal, black, red, green, yellow, blue, magenta, cyan, white
// Available attributes: bold, dim, ul (underline), blink, reverse (swap foreground and background)
1st: foreground color
2nd: background color
3rd: attribute
```
---
**DIFF**
```
git config --global color.diff.meta "blue black bold"
git config --global color.diff.frag "magenta bold"
git config --global color.diff.old "red bold"
git config --global color.diff.new "green bold"
git config --global color.diff.context "#999999"
git config --global color.diff.func "#cc99cc"
```
```
[color "diff"]
    meta = blue black bold
    frag = magenta bold
    old = red bold
    func = "#cc99cc"
    new = green bold
    context = "#999999"   
```
---
**BRANCH**
```
git config --global color.branch.current "yellow reverse"
git config --global color.branch.local "yellow"
git config --global color.branch.remote "green"
```
---
**STATUS**
```
git config --global color.status.added "yellow"
git config --global color.status.changed "green"
git config --global color.status.untracked "cyan"
```
