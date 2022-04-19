<p align="center">
    <image src="images/cover.png">
</p>

# Git Essentials

Git is a Version Control System(VCS), aka Source Code Management(SCM).

## History of VCS Tools:

1. Source Code Control System(SCCS):
    - 1972
    - closed-source
    - only Unix support
    - supported text files
    - stored original version file and sets of changes
    - one user could work on a file at a time (local repository)
2. Revision Control System(RCS):
    - 1982
    - open-source
    - cross-platform
    - supported text files
    - stored latest version file and sets of changes
    - one user could work on a file at a time (local repository)
3. Concurrent Versions System(RCS):
    - 1986-1990
    - open-source
    - cross-platform
    - supported text files
    - stored all versions of the files
    - multi-user repositories (remote repositories)
4. Apache Subversion(SVN):
    - 2000
    - open-source
    - cross-platform
    - supported text and image files
    - directory based tracking
    - multi-user repositories (remote repositories)
5. Bitkeeper SCM:
    - 2000
    - similar to SVN
    - closed-source, proprietary
    - distributed version control
    - community version was free
    - used for source code of Linux kernel from 2002 to 2005
    - controversial to use proprietary SCM for open-source project
    - April 2005: the community version was not free anymore
6. Git:
    - April 2005
    - created by Linus Torvalds(also created Linux)
    - replacement for Bitkeeper for Linux source code management
    - distributed version control
    - open-source and free software
    - faster than other SCMs
    - better safeguards against data corruption

<br>

## Github:
- 2008
- hosts Git repositories
- purchased by Microsoft in 2018

<br>

## Distributed Version Control:
- different users maintain their own repositories
- no single central or master repository
- changes are stored as change sets
- tracks changes and not versions unlike CVS and SVN
- change sets can be exchanged between repositories ("merge-in change sets" or "apply patches")

### Advantages of Distributed Version Control:
- no need to communicate with a central server
- faster than other traditional version control systems
- no network access required
- no single failure point
- encourages participation and forking of projects
- developers can work independently
- submit change sets for inclusion or rejection

<br>

## Architecture:

- Git uses **Three Tree Architecture** as opposed to other VCSs that use traditional **Two Tree Architecture**

Two Tree Architecture - Traditional        |  Three Tree Architecture - Git
:-----------------------------------------:|:-----------------------------------------:
![](images/two-tree-architecture.png)      |  ![](images/three-tier-architecture.png)

<br>

## Git Workflow:

- Make changes
- Stage changes
- Commit changes

<br>
<p align="center">
    <image src="images/git-workflow.gif">
</p>
<p align="center">
    <b>Sample Workflow - </b>Involving three changes A, B, C
</p>
<br>

## Git Configuration:

1. System Config File-
    - Scope&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:&nbsp;`git config --system`
    - Win Path&nbsp;:&nbsp;`Program Files\Git\etc\gitconfig`
    - Mac Path&nbsp;:&nbsp;`etc\gitconfig`

2. User Config File-
    - Scope&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:&nbsp;`git config --global`
    - Win Path&nbsp;:&nbsp;`Users\<user_name>\.gitconfig`
    - Mac Path&nbsp;:&nbsp;`$Home\.gitconfig`

3. Project Config File-
    - Scope&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:&nbsp;`git config`
    - Path&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:&nbsp;`my_project\.git\config`

<br>

## Tree-ish: 

The following git objects qualify as a **tree-ish**:
- SHA-1 hash
- HEAD pointer reference
- Branch reference
- Tag reference
- Ancestry

> Use ^ to refer to the ancestors of a commit
>- parent - `git show HEAD^` or `git show HEAD~1`
>- grandparent - `git show HEAD^^` or `git show HEAD~2`
>- great-grandparent - `git show HEAD^^^` or `git show HEAD~3`

<br>

## Commonly Used Commands:

### Set configuration:
    
    git config --global <config_name> <value>

    git config --global user.name "Ashutosh Ojha"

    git config --global user.email "ashutosh.ojha2009@gmail.com"

    git config --global core.editor "atom --wait"
    
    git config --global color.ui true


### Show configuration:
    
    // lists all config properties
    git config --list

    // shows a specific configuration property
    git config <config_property>

    // shows a user name
    git config user.name


### Show command manual:
    
    git help <command_name>

    man git-<command_name>


### Initialize repository:
    
    // adds .git to directory
    // converts a normal directory into a repository
    git init 


### Get repository status:
    
    // gives status info like edited, staged, unstaged and untracked files
    git status


### Stage changes:
    
    git add <change_path>

    // stages all changed files in the directory
    git add .

    // stages a specific change
    git add changed_file.txt 

    // stages multiple files
    git add changed_file_1.txt changed_file_2.txt


### Commit changes:

    // makes the staged changes permanent and tracks them
    git commit

    // commit with a message
    git commit -m "<message>"

    // commit with a message and additional descriptions
    git commit -m "<message>" "<desc1>" "<desc2>"
    
    // amend or modify the most recent commit
    git commit --amend -m "<message>"


### Stage and Commit shortcut:

    // directly commits all the changes(no manual staging needed)
    // commits all changes(staged and unstaged) except untracked changes
    git commit -a
    git commit --all
    
    // commits all changes with a message
    git commit -am "<message>"


### View commit log:

    // lists all the commits
    git log
    
    // limits the number of commits to be shown
    git log -n <limit>

    // filter by date
    git log --since=<date1> --until=<date2>
    
    // filter by author name
    git log --author="<author_name>"

    // filter all the meta data of the commits using regex 
    git log --grep="<regex>"

    // filter by a range
    git log <commit_1_id>..<commit_2_id>

    // filter by file
    git log <file>

    // formatting logs
    // shows changes in form of change-sets or patches
    git log -p

    // formats log to give a statistical view
    // shows the files changed and number of insertions(+) and deletions(-) in the files
    git log --stat

    // other formats: oneline, medium(default), full, fuller, email, raw
    // gives shorter description of commits
    git log --format=short

    // show commits with one-line commit messages
    // better than using --format=oneline
    // ignores the descriptions
    // shortens the commit id
    git log --oneline

    // provides a graphical view
    // useful when multiple branches are present
    git log --graph

    // best combination of formatters
    git log --graph --all --oneline --decorate


### Show specific commit:

    // shows all the changes(git diff) done in a particular commit
    // need not type entire 40 character commit id, first few characters also work
    git show <commit_id>


### View changes in tree-ishes:
    
    // shows difference between old and new version of each file

    // lists differences in all modified files
    // shows the line by line difference between file versions
    // compares working directory version against staging tree version of the files
    git diff

    // shows and highlights word by word difference
    git diff --color-words

    // shows difference in a specific modified file
    git diff changed_file.txt 

    // shows difference in multiple modified files
    git reset changed_file_1.txt changed_file_2.txt

    // compares staging tree version against repository version of the files (staged/cached)
    git diff --staged
    git diff --cached

    // view differences between commits
    // HEAD can be used instead of the commit id to point to the latest commit 
    git diff <commit_1_id>..<commit_2_id>

    // view differences between branches
    git diff <branch_1>..<branch_2>

    // hit 'q' to exit out of diff view


### Delete files:

    // stages deleted file if manually deleted
    git rm <deleted_file>
        
    // permanently deletes and stages a file
    git rm <to_be_deleted_file>


### Moving or Renaming files:

    // manually moving or renaming a file is identified as deleting old file and adding new file
    // upon staging it is recognized as rename operation
    // moving a file using command line is identified as renaming and is automatically staged

    // renaming file name
    git mv <old_file_name> <new_file_name>

    // moving a file
    git mv <old_file_name> <new_path/old_file_name>


### Undo changes:

    // undo changes in working directory
    // restores the repository version of a file from current branch
    git checkout -- <file>

    // retrieve old versions of files using commit id
    git checkout <commit_id> -- <file>

    // revert commit
    // reverts the change done in the specified commit
    git revert <commit_id>

### Remove untracked files:

    // performs a dry run and informs which files would be deleted
    git clean -n

    // actually deletes the untracked files
    git clean -f
    
    // remove untracked files in an interactive way
    git clean -i
    
### List the directory contents:
    
    // lists the directories and files under a tree-ish(commit, branch, etc)
    // a file is labeled as blob(binary large object)
    // a directory is labeled as tree
    git ls-tree <tree-ish>

    // list the content of a specific directory under a tree-ish
    git ls-tree <tree-ish> <path/>

### Create and switch branch:

    // lists all the branches in the repository
    git branch

    // lists all the branches that have their commits merged in current branch
    git branch --merged

    // lists all the branches whose commits are not merged in current branch
    git branch --no-merged

    // create a new branch
    // allowed characters for branch name: [a-zA-Z0-9_]*
    git branch <new_branch>

    // swtich to a branch
    git checkout <branch_name>

    // create and switch in one go
    git checkout -b <new_branch>    
    
> Note:-
> - Cannot switch branch if changes in working directory conflict
> - Can switch branch if changes in working directory can be applied without conflict
> - Can switch branch if files are not being tracked
> - To switch branch with uncommited changes:
>   - Commit the changes to the current branch
>   - Remove the changes, checkout the files again
>   - Stash the changes
> - Install git-prompt.sh to configure command prompt to show the current branch.

### Rename branch:

    // renames the old branch with a new branch name
    // does not require the old branch to be checked out
    git branch -m <old_branch> <new_branch>

    // renaming the current checked out branch
    git branch -m <new_branch>

### Delete branch:

    // deletes the specified branch
    // can specify more than one branch names to be deleted
    // cannot delete the current checked out branch
    // cannot delete a branch with commits that have not been merged
    git branch -d <branch>

    // to delete a branch with unmerged commits
    git branch -D <branch>

### Reset:

    // soft reset
    // similar to git commit --amend
    // moves HEAD pointer
    // does not change staging index or working directory
    git reset --soft <tree-ish>

    // mixed reset
    // default choice
    // moves HEAD pointer
    // changes staging index to match repository
    // does not change working directory
    git reset --mixed <tree-ish>

    // hard reset
    // moves HEAD pointer
    // changes both staging index & working directory to match repository
    git reset --hard <tree-ish>

### Merge:

    // merge new branch into current branch
    git merge <new_branch>

    // in case of merge conflicts:
    // abort the merge
    git merge --abort

    // after resolving conflicts
    git add <conflicted_files>
    git commit

### Stash:

    // creates a new stash named stash_name
    // moves the changes from working directory to the stash
    // untracked changes are not stashed by default
    git stash save <stash_name>

    // to stash untracked files too
    git stash -u
    git stash --include-untracked

    // view stashed changes
    // lists all the stashes by name
    git stash list

    // show the changes in a particular stash
    // lists all the modified files along with the changes as stats
    git stash show <stash_id>

    // to show the line-by-line changes
    git stash show -p <stash_id>

    // retrieve stash
    // applies the changes of a stash to current branch's working directory
    git stash apply <stash_id>

    // applies and removes a specific stash 
    // the newest stash is popped if stash_id is not provided
    git stash pop
    git stash pop <stash_id>

    // delete stash
    // removes a specific stash
    git stash drop <stash_id>

    // clears the stash list completely
    git stash clear


> Note:
> - Similar to merge, while applying a stash, conflicts might occur.
> - The conflicts are handled similar to merge conflicts.

## Remote Repositories:

### Show remote:

    // lists all added remotes
    git remote
    
    // shows remotes used for fetch and push
    git remote -v

### Add remote:

    // adds a remote repo url as origin
    git remote add origin <url>

### Delete remote:

    // removes the remote
    git remote rm origin

### Create remote branch:

    // local branches need to be pushed individually
    // locally checkout branch to be created on remote
    git push -u origin <branch>
    