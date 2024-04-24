# This is a practice repository with Hahow course: **Git - 軟體工程師必備的版本管理時光機** 

## common commands
- **git add \<file>**
    stage the changed files (add it to the index) 
- **git commit -m '\<Commit Message>'**
- **git push -u origin \<branchname>**

## checkout 
- **git checkout \<sha1>**  
    check out a particular commit
    > <sha1> is the commit unique number ([SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash value) that you can obtain with git log.
- **git checkout \<sha1> \<file>**  
    check out a file from a particular commit
- **git checkout HEAD \<file>**  
    equivalent to **git checkout -- \<file>**
    resume the file to the status before added
- **git cherry-pick \<sha1>**  
    applies the changes introduced by the named commit on  the **HEAD** branch

## reset
Reset the content from a particular commit.  
[Git Reset Explanation Video](https://www.youtube.com/watch?v=s1idhUiCk38)  
    
- **git reset --hard \<sha1>**  
    uncommit + unstage + delete changes, nothing left  
- **git reset --mixed \<sha1>** //default  
    uncommit + unstage changes, changes are left in working tree  
- **git reset --soft \<sha1>**  
    uncommit changes, changes are left staged (index)


## branch 
- **git checkout \<branchname>**  
    check out a branch  
- **git branch \<branchname>**  
    make a new branch at the current commit  
- **git branch \<branchname> \<sha1>**  
    make a new branch at a particular commit  
- **git branch -D \<branchname>**  
    delete a branch or multiple branches  
    *ex: git branch -D bn1 bn2*  
- **git push origin --delete \<branchname>**  
    delete a *remote* branch  

## merge
- **git merge \<branchname>**  
    integrates changes from another branch to the **HEAD** branch  
    > Automatic merge failed:  
    Might have to fix conflicts, the conflicted files will contain content of both paths. 
- **git merge --abort**  
    cancel merge operation if there are unmerged paths from a merge conflict  
- **git merge \<branchname>**  
    integrates changes from another branch to the **HEAD** branch  
    
## rebase
There is no difference in the end product of the integration between merging and rebasing, but rebasing makes for a cleaner history.
- **git rebase \<branchname>**
    Take all the changes that were committed on the current branch and replay them on a particular branch


## reference logs
Reference logs, or "reflogs", record when the tips of branches and other references were updated in the local repository.
- **git reflog**  
    equivalent to **git reflog show HEAD**
    show the log of the reference provided in the command-line (or HEAD, by default)

## stash
- **git stash**
    save your local modifications away and revert the working directory to match the **HEAD** commit
- **git stash list**
    view created stashes
- **git stash pop \<stash identifier>** //default newest stash
    remove the changes from your stash and reapply them  
- **git stash drop \<stash identifier>** //default newest stash
    delete a stash