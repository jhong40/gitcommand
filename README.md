# gitcommand

## main
```
git add .
git commit -m "blah"
git status
git diff
git diff --color-word
```

## auto complete
```
github.com/git/git
contrib/completion/git-completion.bash
```

## common commands
```
## Git Log
git help log
man git-log
git log -n 5  # same as git log -5 
git log --since=2019-01-01
git log --until=2020-01-01
git log --until="3 days ago"
git log --after=2.weeks --before=3.days
git log --author="Kevin"
git log --grep="Init"
git log cmit#1..cmit#2
git log cmit#1..HEAD
git log file1  #show all the cmit on this file
git log -p #show cmit info, also with the exact changes  -p stadnds for patch or change
git log --stat   #show how many changes, not what changes
git log --foramt=oneline  # online, short, medium, full, fuller, etc
git log --online # reduce long sha to short sha
git log --graph
git log --graph --all --oneline --decorate

# HEAD
refs/head/master
git diff  #compare working dir to starging by default
git diff --stage #compare staging and repo
git diff --cache #same as above

git rm file1
git commit -m "delete file1"

## rename
mv first.txt primary.txt
git status # show 2 changes: 1 is delete first.txt, 2: add primary.txt
git rm first.txt
git add primary.txt
git status # git regonize and show rename first.txt to primary.txt

git mv secondary.txt secondary.txt # change the file in working txt, and take it to staging

git commit -am "msg" # doesn't add new file
git show cmit# --color-words
git diff cmit#1..cmit#2  --color-words #compare 2 commit
git diff cmit#..HEAD

git commit -a  # multi-line message: 1st line - summary, 2nd line - blank, 3rd - more lines

## discard change
git checkout -- file1  # grab file1 from repo to cur dir
git checkout -- . # grab all from repo to cur dir

## Unstaging file
git add file1 
git reset HEAD file  # mv it from staging 

## amend commit
git add file1
git commit -m 'file1 change1"
# make change to file1 
git commit -m "file1 change2"
git commit -amend -m "file change2"
git status # show "file change2" msg with chang1 and change2
#make no change, just change the cmt msg
git commit -amend -m "file1 another change"
git stauts # show "file1 another change" msg with change1 and change2


## Retrive Old version
git checkout cmit# -- file1.txt  
git status  #show file1.txt in staging and cur dir

# make change to file1
git add file1
git reset HEAD file1  # remove from staging to working dir
git checkout -- file1  # overwrite it from repo

# revert change
git revert cmit#

# remove untracked files
git clean  # -i -n -f
git clean -n # dry run
git clean -f

### .gitignore
https://github.com/github/github
project/.gitignore

git config --global core.execludesfile ~/.gitignore_global

git rm --cache file1 # rm from staging, not working dir
git ls-tree HEAD


```

## Ancestry- Parents
```
de1461f^  #parent of cmt de1461f
HEAD^  # parent of HEAD
master^
HEAD~1, HEAD~   #parent of HEAD
git show HEAD^

^^  #parent of parent
de1461f^^
HEAD^^
HEAD~2 # parent of parent of HEAD
git show HEAD^^

git show HEAD~2
git show HEAD~3


## ls-tree
git ls-tree HEAD
git ls-tree HEAD folder1   #list just the folder
git ls-tree HEAD folder1/  #list all files under folder1

```
## Branch
```
git branch  #show branches
git branch new_feature
cat .git/HEAD #show head 
root@kubernetes01:~/gitpractice/.git/refs/heads# ls -tlr
total 8
-rw-r--r-- 1 root root 41 Jul 21 16:21 master
-rw-r--r-- 1 root root 41 Jul 21 17:12 new_feature

git checkout new_feature
git branch
root@kubernetes01:~/gitpractice# git branch
  master
* new_feature
root@kubernetes01:~/gitpractice# cat .git/HEAD
ref: refs/heads/new_feature

git checkout -b branch1 # create new branch1 and checkout

## cannt switch to a branch: commit to the current branch, remove it, stash

# compare branches
git diff --color-words new_feature..short
git branch --merged
git branch --no-merged

root@kubernetes01:~/gitpractice# git branch
  master
  new_feature
* short
root@kubernetes01:~/gitpractice# git branch --merged
  master
  new_feature
* short

root@kubernetes01:~/gitpractice# git checkout new_feature
Switched to branch 'new_feature'
root@kubernetes01:~/gitpractice# git branch --merged
  master
* new_feature
root@kubernetes01:~/gitpractice# git branch --no-merged
  short


# Rename Branch
root@kubernetes01:~/gitpractice# git branch
  master
* new_feature
  short
root@kubernetes01:~/gitpractice# git branch -m seo_feature
root@kubernetes01:~/gitpractice# git branch
  master
* seo_feature
  short
# git branch -m br1 br2   # even without checkout br1  

# Delete Branch
root@kubernetes01:~/gitpractice# git checkout master
Switched to branch 'master'
root@kubernetes01:~/gitpractice# git branch branch2delete
root@kubernetes01:~/gitpractice# git branch
  branch2delete
* master
  seo_feature
  short
root@kubernetes01:~/gitpractice# git branch -d branch2delete
Deleted branch branch2delete (was a6aabc6).
root@kubernetes01:~/gitpractice# git branch
* master
  seo_feature
  short

git branch -D branch2delete   # if any un merged commit in it

# git prompt
https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh

```

### Reset Types
+ Soft Reset: Move HEAD, Doesn't change staging index, cur dir 
```
git reset --soft <tree-is>

[root@kubernetes01 gitpractice (master)]# git branch
* master
  seo_feature
  short
[root@kubernetes01 gitpractice (master)]# git checkout -b reset_branch short
Switched to a new branch 'reset_branch'
[root@kubernetes01 gitpractice (reset_branch)]# git branch
  master
* reset_branch
  seo_feature
  short
[root@kubernetes01 gitpractice (reset_branch)]# git log -1
commit 127ea2841dd0e8ccffc7925b12cf6c1056cb3003 (HEAD -> reset_branch, short)
Author: Jack.Liu <blah@blah.com>
Date:   Wed Jul 21 17:30:55 2021 -0400

    another
[root@kubernetes01 gitpractice (reset_branch)]#

```
+ Mixed Reset: Move HEAD, Change staging index, Doesn't change working dir
```
git reset --mixed tree-ish  #defult as git reset tree-ish
```
