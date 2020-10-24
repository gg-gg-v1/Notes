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
