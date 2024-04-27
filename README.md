# This is a practice repository with Hahow course: **Git - 軟體工程師必備的版本管理時光機** 

::: info
**course tool:** [installation tutorial link](https://gist.github.com/kewang/8c478078f2a98f32f5bcbfca1348a8a1#file-readme-md)  
git tree .  
ctrl+b then press d to leave git-tree
:::

## common commands
- **git remote add origin \<remote repository url>**  
    add the remote repository to push/pull files to/from  
- **git remote -v**  
    show remote url after name  
- **git add \<file>**  
    stage the changed files (add it to the index)  
- **git commit -m '\<commit message>'**  
- **git push -u origin \<branchname>**  
- **git pull**  
- **git fetch**  
- **git show \<sha1>**  
    <sha1> is the commit unique number ([SHA-1](https://en.wikipedia.org/wiki/SHA-1) hash value) that you can obtain with git log  
- **git log \<sha1>**  
- **git log \<file>**  
- **git blame \<file>**  
    git log shows the commit hash and author of each commit, while git blame shows the commit hash and author of each line in the file  

## search
- **git diff**  
    show difference of all unstaged files  
- **git diff --cached**  
    show difference of all staged files  
- **git diff --name-status**  
    show difference of how the unstaged files are changed  
- **git log -S \<keyword>**  
    search for commits that contains \<keyword> (capital sensitive)  
- **git log --since=2024/4/24 --until=2024/4/25**  
- **git log --author=\<author name or author email>**  
- **git log -n \<number>**  
- **git log --all --decorate --oneline --graph --color=always**  
    similar to the git tree . tool provided at the beginning  

## check out/apply/revert changes 
- **git checkout \<sha1>**  
    check out a particular commit  
- **git checkout \<sha1> \<file>**  
    check out a file from a particular commit  
- **git checkout HEAD \<file>**  
    equivalent to **git checkout -- \<file>**  
    resume the file to the status before added  
- **git cherry-pick \<sha1>**  
    apply the changes introduced by the named commit on  the **HEAD** branch  
- **git revert \<sha1>**  
    create a new commit that apply the inverse of a particular commit  
- **git revert \<sha1>^..\<sha1>**  
    create a new commit that apply the inverse of all changes between two commits  
- **git revert --no-commit \<sha1>**  
    apply the inverse of a particular commit  

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
- **git branch -av**  
    -a: all  
    -v: verbose  
- **git branch -D \<branchname>**  
    delete a branch or multiple branches  
    *ex: git branch -D bn1 bn2*  
- **git push origin --delete \<branchname>**  
    delete a *remote* branch  
- **git push origin :\<branchname>**  
    make the branch on the remote *nothing*, which deletes it  
    see more in [The Refspec](https://git-scm.com/book/en/v2/Git-Internals-The-Refspec)  
- **git remote prune origin**  
    delete the refs to branches that don't exist on the remote  
- **git fetch --prune**  
    same as **git remote prune origin**, but before pruneing, the latest remote data is first fetched  

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

## restore
- **git restore \<file>**  
    discard uncommitted local changes in a file. **Cannot undo!**  
- **git restore --stage \<file>**  
    unstage a certain file and thereby undo a previous git add  
- **git restore --source \<sha1> \<file>**  
    restore the file as it was in a particular commit  
    
## searching for a commit
- **git bisect start** to start  
- **git bisect reset** to end  
    remember to reset even if the commit is found  
- **git bisect bad** to mark bad version  
- **git bisect good** to mark good version  
git bisect would mark commits and keep finding the exact commit that started to go wrong, like a binary search  

## .gitignore
a file specifies intentionally untracked files that Git should ignore  
example:
```
.DS_Store
*.tmp
*.bak
```
[gitignore.io](gitignore.io) can help create useful .gitignore files for your project