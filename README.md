# BasicGitCommand
    -  It is a free and open-source version control system used to handle small to very large
       projects efficiently. Git is used to tracking changes in the source code, enabling multiple 
       developers to work together on non-linear development.


# Basic Commands for Git Version control


1. git config --global user.name "sheeshpal" -> Set user name.
2. git config --global user.email "example@gmail.com" -> set email.
3. git init -> initialize git repository
4. git clone < repo-address > -> clone/getch/download repo from github.
5. git add "filename" -> track file by git.
6. git add . -> track all file by git.
7. git commit -m "any message to commit" -> save tracking record.
8. git status -> tell current status about git repository.
9. git remote add origin < address remote repo> -> add remote repo.
10. git remote -> show remote location name like origin.
11. git git remote -v -> show where to fetch and push data.
12. git branch "newBranchName" -> create new branch.
13. git branch "newBranchName" hashCode -> create Branch from any commit by hash code.
14. git checkout "branchName" -> Change brnach name.
15. git branch -d "branchName" -> delete branch into local machine.
16. git push -d origin "branchName" -> delelte branch into remote location.
17. git push -u origin master/main.
18. git push -u origin "branchName" -> push other branch, if not exit into remote then it create.
19. git push --all origin -> push all branch at origin.
20. git pull -> fetch all changes from remote to local working directory.
21. git merge < branchName > -> merge branch into current branch.
22. git log -> show all commit
23. git log -1 -> show last one commit.
24. git log -2 -> show last two commit.
25. git log --oneline -> show all commit in short
26. git branch -M newBranchName -> change branch name.



# Conflict in git
when change same thing in two or more branch with different content 
and try to merge it then it show to us a conflict.

    - we can decide which change preserve or which one not. -> resolve conflict.

    resolve: remove those thing which do you not want to same.
    then commit again.


# .gitignore
    - it ignore by the git, and git doesn't track to it.
    - use for ignore the file by git.
    - generaly use for ignore large file which is not required.
    
    make a .gitignore file and write down all the file inside it.
    and it basically ignore all these file[ only mention inside it ]


# Skipping the staging area :
    git add .
    git add -A
    git add -u  //these three command are same.

    Difference in these command [Git version 2.x]

    command         NewFile        ModifyFile        DeleteFile     Description
    git add -A      right           right              right        stage All[new,delete,modify]

    git add .       right           right              right        stage all

    git add -u      no              right               right       stage modified and delete file only


    

# Gid Diff command :

    wd -> working directory
    sa -> staging Area
    LR -> local repository.

    Showing changes between WD & SA,  WD & LR, SA & LR 

    Working Dir     Staging Area/cache Area       Local Repo/Committed Area

     |------ git diff-------|-------git diff --staged[git diff --cached]--|
     |                                                                    |
     |------------------git diff head[git diff head]----------------------|


# Renaming and Remove file :
## Rename:
    Normal way is by right click and rename then stage and commit.

    By git command :
        git mv file4.text file3.text    // rename fiel and come into stage area.

## Delete/Remove :
    Normal way is by right click on file and delete

    by git command:
        git rm file2.txt        //remove file
        git rm --cached file1.text      //remove file from staging area.


# UnStaging and UnModifying Files changes in Git :
    Discard the changes in working file and adding in staging area.


    git add <fileName>... -> update what will be committed

    git restore <fileName>... -> to discard changes in working directory



# Reset command : --hard, --soft, and --mixed 

    All commits have its own hashcode which is unique in all of them.

    by misstake if we commit some changes we can roll back our commit to its previous commits

    ** reset is dangerous for uses because if it reset the commit then it delete to that we can't
    got it again. 

    

    -> for using reset we used three option
        - --hard
        - --shoft
        - --mixed


        example: with hard option
        
        git reset --hard <hashcode>        //remove commit from local reop.

        //for remove from remote also need to push
        git push -u origin master       // it show error bcz our branch is behind by one commit.

        //now we need to push code forcefully with -f option
        git push -f -u origin master    //now it push the code at remote forcefully.


        example: with soft option
        git reset --soft <hashcode>         //remove from commit and come up in staging area.

        git rm --cached file1 file2         //remove from track by git

        //for remove file from the untrack by git
        git clean -n        //show all file which in untrack we can delete those file
        git clean -d -i     //delete recursivly



# Revert command :
    git revert <hashcode>       // make a new commit after changes of above given hashcode.

    //now our repo is ahead one commit form the remote repo.



    //now for get deleted commited revert new revert commit

    git revert <hashcode> 

    //we can delete commit with a range.

    git revert <starting_commit_hashcode>^..<last_commit_hashcode>      //need to provide manula msg

    //we can give same commit for all the rage deleted commit for save time

    git revert --no-commit <startHashcode>^..<lastHashcode>     // all file come up into staging area with deleted file.
                                                                //now need to commit these deleted file.