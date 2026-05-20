# lets start !

This is a simple project to learn how to use git and github.

# first we need to initialize a git repository in our project folder:
- **git init**

- **U** = untracked file
- **A** = added file
- **M** = modified file
- **D** = deleted file
- **R** = renamed file
 
# Check Logs 
- check the logs : **git log --oneline**
- check the logs with details : **git log**
- check the logs with more details : **git log -p**

# Git Status
- check stage of a file: **git status -s**
- check all changes: **git status**

# Previous commit
- git checkout HEAD~1
- git checkout HEAD~2

# Branching
- create a new branch: **git branch <branch_name>** (git branch feature1)
- switch to a branch: **git switch <branch_name>** (git switch feature1)
- Switch to main branch: **git switch main**

# Delete a branch
- delete a branch: **git branch -d <branch_name>** (git branch -d feature1)
- force delete a branch: **git branch -D <branch_name>** (git branch -D feature1)

# Merge
- you need to be at main branch
- git meger <branch_name> (**git merge feature/calc**)
- ffm = fast forward merge = when there are no changes in the main branch and you can simply move the pointer to the new branch.
- 3 way merge = when there are changes in both branches

# Conflicts
- when there are changes in both branches, git will not be able to merge the branches and will show a conflict.
- you need to resolve the conflict manually by editing the file and then add the file to the staging area and then commit the changes.
- after resolving the conflict, you can merge the branches again.
- git will show the conflict in the file with <<<<<<<, =======, >>>>>>> markers.
- you need to remove these markers and keep the changes that you want to keep and then add the file to the staging area and then commit the changes.
- after resolving the conflict, you can merge the branches again. 

# Stashing
- git stash => this command will save your changes in a stash and will revert your working directory to the last commit.
- git stash list => this command will show you the list of stashes that you have created.
- git stash apply => this command will apply the changes from the stash to your working directory.
- git stash clear => this command will clear all the stashes that you have created.