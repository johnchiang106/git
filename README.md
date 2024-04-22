# This is a practice repository with Hahow course: **Git - 軟體工程師必備的版本管理時光機** 

## git checkout 
- **git checkout <sha1>**
    check out a particular commit
    > <sha1> is the commit unique number ([SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash value) that you can obtain with git log.
- **git checkout <sha1> <file>**
    check out a file from a particular commit
- **git checkout HEAD <file>**
    equivalent to **git checkout -- <file>**
    resume the file to the status before added
- **git reset --hard <sha1>**
    resets the content from a particular commit

## git branch 
- **git branch <branchname>**
    make a new branch at the current commit
- **git branch <branchname> <sha1>**
    make a new branch at a particular commit
- **git branch -D <branchname>**
    delete a branch or multiple branches
    > ex: git branch -D bn1 bn2
- **git checkout <branchname>**
    check out a branch

## git merge
- **git merge <branchname>**
    integrates changes from another branch to the **HEAD** branch