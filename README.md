<details>
  <summary markdown="span">Low Level</summary>
 
 # gitcommand
![image](https://user-images.githubusercontent.com/13383120/232651418-536fedf8-9a57-4454-b463-ee5ae5cbc2f0.png)

![image](https://user-images.githubusercontent.com/13383120/232650059-c1c55167-d99a-4686-adb2-87d1d3f222cf.png)
![image](https://user-images.githubusercontent.com/13383120/232650767-1b21a2d7-65ef-4ee0-a22f-83f09f0d588f.png)

![image](https://user-images.githubusercontent.com/13383120/232651833-b824bd00-4a99-41ed-852d-9c88ef3e7649.png)
![image](https://user-images.githubusercontent.com/13383120/232652126-43f422de-480c-49d5-8ac8-46ab4fef92ea.png)
![image](https://user-images.githubusercontent.com/13383120/232653851-a41e70d4-cbfd-4d44-a30b-80dd2c3a3c62.png)



##
```
git rm --cached file3.txt    # remove file3.txt from stage
git ls-files  [-s]  # display stage files

```

## git low level
```



echo "Hello, Git" | git hash-object --stdin -w  # b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
git cat-file -p b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
Hello, Git
 git cat-file -s b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
11
git cat-file -t b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
blob

echo "Second file in Git repository" > new-file.txt
git hash-object ../new-file.txt
4400aae52a27341314f423095846b1f215a7cf08

git hash-object ../new-file.txt -w 
4400aae52a27341314f423095846b1f215a7cf08

vagrant@vagrant:~/test/.git/objects$ ls -tlr
total 16
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:00 pack
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:00 info
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:16 b7
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:47 44

git cat-file -p 4400aae52a27341314f423095846b1f215a7cf08
Second file in Git repository

vagrant@vagrant:~/test$ cat ../temp-tree.txt
100644 blob b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e    file1.txt
100644 blob 4400aae52a27341314f423095846b1f215a7cf08    file2.txt
vagrant@vagrant:~/test$ cat ../temp-tree.txt  | git mktree
3b95df0ac6365c72e9b0ff6c449645c87e6e1159
vagrant@vagrant:~/test$

vagrant@vagrant:~/test/.git/objects$ ls -tlr
total 20
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:00 pack
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:00 info
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:16 b7
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 01:47 44
drwxrwxr-x 2 vagrant vagrant 4096 Apr 18 02:17 3b
vagrant@vagrant:~/test/.git/objects/3b$ ls -tlr
total 4
-r--r--r-- 1 vagrant vagrant 80 Apr 18 02:17 95df0ac6365c72e9b0ff6c449645c87e6e1159

vagrant@vagrant:~/test/.git/objects/3b$ git cat-file -p 3b95df0ac6365c72e9b0ff6c449645c87e6e1159
100644 blob b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e    file1.txt
100644 blob 4400aae52a27341314f423095846b1f215a7cf08    file2.txt
vagrant@vagrant:~/test/.git/objects/3b$
```
![image](https://user-images.githubusercontent.com/13383120/232655279-0544da61-e117-4a77-ab7e-85890e617d2c.png)
![image](https://user-images.githubusercontent.com/13383120/232655143-13003484-aef2-4762-b763-26f6f1b571e3.png)
```
vagrant@vagrant:~/test$ find .git/objects -type f
.git/objects/3b/95df0ac6365c72e9b0ff6c449645c87e6e1159
.git/objects/44/00aae52a27341314f423095846b1f215a7cf08
.git/objects/b7/aec520dec0a7516c18eb4c68b64ae1eb9b5a5e
vagrant@vagrant:~/test$ git cat-file 3b95 -t
tree
vagrant@vagrant:~/test$ git read-tree 3b95    # read from git repo -> staging
vagrant@vagrant:~/test$ git ls-files          # list staging 
file1.txt
file2.txt
vagrant@vagrant:~/test$ git ls-files -s
100644 b7aec520dec0a7516c18eb4c68b64ae1eb9b5a5e 0       file1.txt
100644 4400aae52a27341314f423095846b1f215a7cf08 0       file2.txt
vagrant@vagrant:~/test$
```
![image](https://user-images.githubusercontent.com/13383120/232656546-294784e0-2255-4156-a318-7ab8f804b884.png)

```
vagrant@vagrant:~/test$ git checkout-index -a    # staging -> working dir
vagrant@vagrant:~/test$ ls -tlr
total 8
-rw-rw-r-- 1 vagrant vagrant 30 Apr 18 02:43 file2.txt
-rw-rw-r-- 1 vagrant vagrant 11 Apr 18 02:43 file1.txt
vagrant@vagrant:~/test$ cat file1.txt
```
![image](https://user-images.githubusercontent.com/13383120/232657172-f55a71b3-a1a2-49b7-a5bb-7207c74e1199.png)


</details>

## Config
```
git config --global user.name "Jack Liu"
git config --global user.email "jack.liu@aaa.com"
git config --global core.editor "notepadd++.exe -multiInst -nosession"  # git config --global -e 
git config --list
cat ~/.gitconfig

```



## main
```
git add .
git commit -m "blah"
git commit -am "blah"   # add and commit 
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
git log -L 100,150:myfile.txt
git log --stat   #show how many changes, not what changes
git log --foramt=oneline  # online, short, medium, full, fuller, etcgit
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
git branch new_feature  # create new new_feature branch, but not switch to it 
cat .git/HEAD #show head 
root@kubernetes01:~/gitpractice/.git/refs/heads# ls -tlr
total 8
-rw-r--r-- 1 root root 41 Jul 21 16:21 master
-rw-r--r-- 1 root root 41 Jul 21 17:12 new_feature

git switch new_feature   # switch to new branch
git switch -c branch1    # create and switch to it

git merged-base br1 br2  # find the common ancestor of both branches

# rename branch
git branch -m mybr newbr   # mybr => newbr
git branch -m newbr        # if in mybr already

# delete branch
git branch -d br1          # delete br1 
git branch -D br1          # delete br1 even if it is not fully merged


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

### Tagging - like a bookmark to a commit
```
git tag issue_123 655da716     # issue_123 tag -> sha 655da716
git tag mytag                  # mytag -> head
git tag -a v1.0 commit#        # will open editor to input msg
git tag -am "Version 1.0" v1.0 commit#    # like git commit -am "aaa"
git tag -d v1.0                # delete the tag, the commit# remains

git tag 
git tag --list                  # same as above
git tag -l                      # same as above

git tag -l "v2.*"
git tag -n

# push tags to remote
git push origin v1.0
git push origin --tags   
git push -d origin v1.0     # delete v1.0 tag from remote
```
### Reset 
+ c1,c2,c3,c4,c5,c6,c7/head/main  reset to c5: c1,c2,c3,c4,c5/head/main    c6,c7 becomes orphan, can be branch to refer to it before reset
+ Soft Reset: Move HEAD/branch, Doesn't change staging index, cur dir 
```
git reset --soft c5

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

# c1,c2,c3,c4,c5, new changes: c6,c7
git reset -soft c5
git add .
git commit -m "aaa"    # this will create new c6 (original c6,c7 will be orphan)

```
+ Mixed Reset: Move HEAD/branch, Change staging index, Doesn't change working dir
```
git reset --mixed c5  # this is the defult as git reset c5
git reset c5          # same as above
```
+ Hard Reset: Move HEAD, Change staging index, Change working dir (return to old state, discard all  code changes)
```
git reset --hard tree-ish  
```

### Merge code
```
git checkout master        # switch to receiving br 1st
git merge br1              # will give the conflict
git merge --abort          # abort the merge
# manually resolve the conflict
git add f1 f2              # 
git commit -m "aaa"        # after this, merge complete


git merge seo_feature
root@kubernetes01:~/gitpractice# git log --oneline
58d4df5 (HEAD -> master, seo_feature) Modifies a.txt in new-feature
a6aabc6 add eee
0a39700 adding more
ad82f87 adding a.txt
root@kubernetes01:~/gitpractice# git diff master..seo_feature
root@kubernetes01:~/gitpractice# git branch --merged
* master
  seo_feature
root@kubernetes01:~/gitpractice#
```

# reslve conflict
```
git merge br1      #

git diff --color-words  master..text_edits a.txt
git show --color-words 
```
## Stash
```
root@kubernetes01:~/gitpractice# git status
On branch short
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")
root@kubernetes01:~/gitpractice# git checkout master
error: Your local changes to the following files would be overwritten by checkout:
        a.txt
Please commit your changes or stash them before you switch branches.
Aborting
root@kubernetes01:~/gitpractice# git stash save "stash1"
Saved working directory and index state On short: stash1
root@kubernetes01:~/gitpractice# git status
On branch short
nothing to commit, working tree clean
root@kubernetes01:~/gitpractice# cat a.txt
iii
ddd
eee
new-feature
short
another change
root@kubernetes01:~/gitpractice# git checkout master
Switched to branch 'master'
root@kubernetes01:~/gitpractice# git checkout short
Switched to branch 'short'
root@kubernetes01:~/gitpractice# git stash list
stash@{0}: On short: stash1
root@kubernetes01:~/gitpractice# git stash show stash@{0}
 a.txt | 1 +
 1 file changed, 1 insertion(+)
root@kubernetes01:~/gitpractice# git stash show -p stash@{0}
diff --git a/a.txt b/a.txt
index c0f1036..ef4a577 100644
--- a/a.txt
+++ b/a.txt
@@ -3,4 +3,5 @@ ddd
 eee
 new-feature
 short
+short1
 another change
root@kubernetes01:~/gitpractice#
root@kubernetes01:~/gitpractice# git stash pop    ## pop remove stash
On branch short
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (6ba9ec2c2844157626ca72286fbe57156cc65eaa)
root@kubernetes01:~/gitpractice#
root@kubernetes01:~/gitpractice# git stash save "another"
Saved working directory and index state On short: another

root@kubernetes01:~/gitpractice# git stash list
stash@{0}: On short: another
root@kubernetes01:~/gitpractice# git stash apply   ## doens't remove stash
On branch short
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   a.txt

no changes added to commit (use "git add" and/or "git commit -a")
root@kubernetes01:~/gitpractice# git stash list
stash@{0}: On short: another
root@kubernetes01:~/gitpractice#

root@kubernetes01:~/gitpractice# git stash list
stash@{0}: On short: another
root@kubernetes01:~/gitpractice# git stash save "Delete me"
Saved working directory and index state On short: Delete me
root@kubernetes01:~/gitpractice# git stash list
stash@{0}: On short: Delete me
stash@{1}: On short: another
root@kubernetes01:~/gitpractice# git stash drop stash@{0}
Dropped stash@{0} (bdfc2ede72cf9c8867155121fd73e75b434afefb)
root@kubernetes01:~/gitpractice# git stash list
stash@{0}: On short: another
root@kubernetes01:~/gitpractice# git stash clear  # delete all the stash
root@kubernetes01:~/gitpractice# git stash list  
root@kubernetes01:~/gitpractice#
```


# Remote
### remote: brancha  tracking branch - origin/brancha, local branch -bracha 
```
#remote branch cannot be check out
git remote add origin https://github.com/....
git remote 
git remote -v
git remote rm origin
git branch -r   # remote branch
git branch -a   # all branch: local and remote

git remote show origin


git clone  https://github.com/jhong40/mytest.git anotherfolder   # cd anotherfolder: you will see the code
git fetch origin         # bring the main from remote to the origin/main
git merge origin/main    # merge the origin/main into local main (assume in local main branch)

git pull = git fetch + git merge 


git checkout master
git fetch
git merge origin/master  #resolve any conflict


git pull # = git fetch + git merge

# push changes to remote
git push remote localbr:remotebr  # generic
git push origin main:main         # example
git push                          # if tracking in place

# create loal branch from remote
git branch brancha origin/brancha  #create branch based on origin/brancha
git checkout brancha origin/brancha

# create remote brach 
git push -u brancha origin     # -u is upstream, tracking

# git config --global push.autoSetupReomte true   # this is to avoid -u everytime. It adds -u automatically.

# delete remote branch
git push orgin :brancha  # delete brancha
git push -d origin brancha   # delete remote brancha, tracking brancha, not local brancha
```
# FLOW
```
## Developer1
git checkout master
git fetch
git merge origin/master
git checkout -b feature1
git add myfile
git commit -m "adding feature1"
git fetch
git push -u feature1 origin

## Developer2
git checkout master
git fetch
git merge origin/master
git checkout -b feature1 origin/feature1
git log
git show sha#
git commit -am "improve feature1"
git fetch
git push   # it is a tracked branch, no need for origial feature1


## Developer1
git fetch
git log -p feature1..origin/feature1
git merge origin/feature1    #ok for the improve feature1
git checkout master
git fetch
git merge origin/master   #if origin/master has change
git merge feature1
git push   # master is tracked, so no origin master

```
# Blame: shows who made the change on that each line, and when
```
git blame file1.txt  # shows who made the change on that each line, and when
git blame -w File1.txt  #ignor white space
git blame -L 100,105 file1.txt
git blame -L 100,+5 file1.txt   #100,105
git blame d9dba0 file1.txt
git blame d9dba0 -- file1.txt

git annotate file1.txt   # similar to blame, diff output format
git config --global alias.praise blame   # praise = blame, git praise file1.txt = git blame file1.txt
```
# bisect: app used to work, not anymore. Need to find which cmt introduing the bug
```
git bisect start
git bisect bad  # git bisect bad HEAD
git bisect good <treeish>  # last known good version

#git will found the mid point version, user need to test and confirm it is good or bad
#git bisect good
#git bisect bad
#eventually it will find the version which introduce the bug

git bisect reset
```

