1. initializse the git repo.
```
Bharats-MacBook-Pro:gitcourse bharat$ git init
Initialized empty Git repository in /Users/bharat/gitcourse/.git/
```
2.  assume u have fileUpload as the repo.

```
git clone https://github.com/gg-gg-codes/fileUpload.git
```
3. ls into this repo on local ...

4. git commit 

```
git commit -m "some git commit message"
```

5. git status 

6. remove the file and commit and push
```

git rm file.txt
git status
git commit -m "some message"
git push
```
7. make copy of the repo in local with below command of clone 

```
 git clone fileUpload/ replicaOfFileUpload
```


EXTRA IMP- >> look for password reset commands
```
git config --global user.email <youremailid>
git config --global user.name <username>
```

8. to see which exactly file got commited
```
git add test1.txt
git commit -m "message"

git write-tree
81581fd44d32f2655d0bd79bb2fc517c4dee593d

git cat-file -p 81581fd44d32f2655d0bd79bb2fc517c4dee593d
100644 blob 81581fd44d32f2655d0bd79bb2fc517c4dee593d	test1.txt
```

9. show the branch
```
git show-branch
```

10. create new branch 'demo'
```
git checkout -b "demo"
```
11. switching to a  branch
```
git checkout master
```
12. current branch in use
```
git branch
```
13. delete the branch, before deleting branch you have to be on another branch e.g. to delete demo branch you have to be on mastaer or develop etc.
```
git branch -d demo
```
14. push new branch to gitrepo..and lets assume master is already created.
```
git push origin HEAD
```

14.1 create new branch lets say branch1 and if u want to push it to repo then do this 
```
git push origin HEAD
```
then you will see new branch branch1 in repo.

14.2 if you want to make changes or push all latest changed in branch1 then do this.
```
git add somefile.txt
git commit -m "somefile is getting added to branch branch1"
git push origin HEAD
OR 
git push
```

14.3 now if you want to merge the branch branch1 to master then do this

```
first switch to master branch
git checkout master
now merge branch1 into master with below command
git merge branch1
```

15. git difference between files
```
git add file1
git commit -m "file1 one old content - foo"

eacho "abc" > file1
git diff
--- a/diff_exmaple/file1
+++ b/diff_exmaple/file1
@@ -1 +1 @@
-foo
+abc
git commit -m "file has been modified" -> now new content will get committed
```

16. git log to see the history of commits
```
git log
```

17.1 merge conflict bw two branches
```
on demo branch
changes file new.txt
git add new.txt
git commit -m "nextxt"
git push
PUSH done on demo branch
now merge this to master
switch to master -> git checkout master
onn master
type
git merge demo
you will see conflicts now if new txt is already present in master so solve it by below method
vi new.txt
make changes and do git add new.txt
again do git commit 
git push
now your branach is merged with new changes
```
17.2 pull issue bw two changes of same branch
```
Bharats-MacBook-Pro:demoRepo bharat$ git push origin HEAD
git: 'credential-wincred' is not a git command. See 'git --help'.
Username for 'https://github.com': gg-gg-codes
Password for 'https://gg-gg-codes@github.com': 
git: 'credential-wincred' is not a git command. See 'git --help'.
To https://github.com/gg-gg-codes/demoRepo.git
 ! [rejected]        HEAD -> demo (fetch first)
error: failed to push some refs to 'https://github.com/gg-gg-codes/demoRepo.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

git pull origin demo
git add new.txt
git commit -m "nextxt"
```

18. push your local branch to remote
git push origin add-edit-api-projectUseCaseServiceFix

19. intellij
commit and push -> you will see your changes but first do the git push origin add-edit-api-projectUseCaseServiceFix


20. push newly created repo to git hub
first add remote origin
```
git remote add origin http://yourmainprojectrepo.git
check via this
git remote
now push new branch to this origin
git push --set-upstream origin my-new-branch

```

21. MERGE conlflicts
```
  139  git merge master
  140  git status
  141  git merge master
  142  git add .
  143  git commit -m "resolving merge conflicts"
  144  git push
  145  git merge master
  146  git checkout master
  147  git merge zalenium-selenium
  148  git push
  149  git status
  150  git add .
  151  git commit -m "formatting pom"
  152  git push
  153  git history
  154  git reflog
  155  history
```

22. Stash GIT
```


This is how you do it:

git stash push -m "my_stash"

Where "my_stash" is the stash name.

Some more useful things to know: All the stashes are stored in a stack. Type:

git stash list

This will list down all your stashes.

To apply a stash and remove it from the stash stack, type:

git stash pop stash@{n}

To apply a stash and keep it in the stash stack, type:

git stash apply stash@{n}

Where n is the index of the stashed change.
```

23. GIT create new branch from specific branch 
```
$ git checkout -b mybranch develop
```

24. git password reset

git config --global credential.helper osxkeychain

then password promt ll come 

25. rename branch
git branch -m oldbranchname newbranchname

26. WORKING with DETACHAED HEAD, if while merging u get this you can follow below steps to resolve this.
```
* (HEAD detached from origin/master)
  jest
  master
```

```
git fetch origin
git checkout -b jest origin/jest

git fetch origin
git checkout origin/master

now if you get this 
HEAD is now at d39387d Merge branch 'revert-b6f0c889' into 'master'

then do this
git merge --no-ff jest
yoou may get merge conflicts, resolve them
commit them
git add .
git commit -m "accepting merge change"
git push origin HEAD:master
```

27. show remote origin url 
```
 git config --get remote.origin.url

```
28. set new git url
```
git remote set-url origin new.git.url/here
```
