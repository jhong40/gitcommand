```
git config --system  # /etc/gitconfig
git config --global  # ~/.gitconfig
git config           # under project  myproject/.git/config

git config --global user.name "John Adams"
git config --global user.email "john.adams@abc.com"
git config --global color.ui true   # show color 
git config --global init.defaultBranch main    # main, master, trunk, development
git config --global core.editor vim   # nano -w, vim, emacs, code --wait, notepad, mate -w

git config --list
```
```
git log  # show some commit
git show ${commit#}  #  show diff of the file b4 commit and after
git show --stat      # show # file changed, # inserts # deletes
```


```
git add .                   # work space => stage
git restore --staged file1  # file1: repo => stg
git diff                    # ws vs stg
git diff --cached           # stg vs repo

git diff --word-diff   # show the word diff... otherwise, it shows the whole changes
git diff --word-diff=color # = git diff --color-words    # show color diff
```
### Add, delete, rename files
```
git rm a.txt                 # ws+stg: remove a.txt 
git mv a.txt b.txt           # ws+stg: a.txt -> b.txt 

git rm --cached a.txt        # stg: rm a.txt
git mv --cached a.txt b.txt  # stg: a.txt -> b.txt

```
### compare commit
```
git log --oneline
git show c1
git diff c1 c2
git diff c1 c2 -- a.txt      # only show a.txt change
git diff --stat c1 c2        # show files changed, # of char changed
```
### Restore to previous version
```
git restore a.txt            # a.txt stg=>ws
git restore .
git restore --staged a.txt;   git restore a.txt  # from repo -> stg -> ws

git restore a.txt --source=c5   # repo => ws  (only impact ws, not repo/stg)
```
### Amend commit
```
git commit --ammend    # it will use the same commit (not create a new commit)
```
### Revert commit
```
git revert c5                # repo: revert back to c5
```
### Remove untracked files
```
git clean -n       # dry run: show untracked files that wourld be removed
git clean -f       # actually remove the untracked files
```
