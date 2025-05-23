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
```


```
git add .  # work space => stage
git restore --stage file1  # stage => workspace
git diff   # working space vs staging
git diff --cached  # staging vs repo

git diff --word-diff   # show the word diff... otherwise, it shows the whole changes
git diff --word-diff=color # = git diff --color-words    # show color diff
```
### Add, delete, rename files
```
git rm a.txt         # remove a.txt from working, and stg
git mv a.txt b.txt   # rename a.txt -> b.txt in both ws and stg
```
