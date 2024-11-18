```
git diff     # work vs stg
git diff --cache   # stg vs repo

git add a.txt   # w -> stg
git commit -m "mm"  # stg -> repo

git rm a.txt  # work, stg
git mv a.txt # work, stg

git rm --cache a.txt  # stg
git mv --cache a.txt #stg

git reset --hard commit3   # repo -> work, stg
git reset --mixed commit3  # repo -> stg
git reset --soft commit3   # repo only

git stash --include-untracked   # (work,stage)=>snapshot
git stash list
git stash apply    # take snapshot => work, stage

git checkout HEAD a.txt   # repo-> work, stage a.txt only file

git add --patch a.txt   # stage part of the file
   # stage this hunk [] ? ?  # type ? to get help
   # y - stage this hunk
   # n - don't stage this hunk
   # s - split into smaller hunk
   # 3 changes, add last one: s, n, n, y


```
