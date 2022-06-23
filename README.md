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

> Note:
> - config can be used to set aliases for commands.
> - Syntax: git config --global alias.<alias_name> <"command">
> - Some popular aliases:
>   - git config --global alias.st "status"
>   - git config --global alias.co "checkout"
>   - git config --global alias.ci "commit"
>   - git config --global alias.br "branch"
>   - git config --global alias.dfs "diff --staged"
>   - git config --global alias.logg "log --graph --decorate --oneline --all"


### Show configuration:
    
    // lists all config properties
    git config --list

    // shows a specific configuration property
    git config <config_property>

    // shows a user name
    git config user.name


### Show command manual:
    
    // git command
    git help <command_name>

    // os command
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

    // stage interactively
    // provides a command line based gui
    // can stage specific files or even specific lines
    git add --interactive
    git add -i

<br>
<p align="center">
    <image src="images/interactive-staging.png">
</p>
<p align="center">
    <b>Interactive Staging</b>
</p>
<br>


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


### View difference between tree-ishes:
    
    // shows difference between two versions of each file

    // lists differences in all modified files
    // shows the line by line difference between file versions
    // compares working directory version against staging tree version of the files
    git diff

    // shows and highlights word by word difference
    git diff --color-words

    // shows difference in a specific modified file
    git diff changed_file.txt 

    // shows difference in multiple modified files
    git diff changed_file_1.txt changed_file_2.txt

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

- Manually moving or renaming a file is identified as deleting old file and adding new file.
- Upon staging it is recognized as rename operation.
- moving a file using `git mv` command is identified as renaming and is automatically staged.

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
> - Cannot switch branch if changes in working directory conflict.
> - Can switch branch if changes in working directory can be applied without conflict.
> - Can switch branch if files are not being tracked.
> - To switch branch with uncommited changes:
>   - Commit the changes to the current branch.
>   - Remove the changes, checkout the files again.
>   - Stash the changes.
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
    // git objects deletion if branch is not merged to other branch
    git branch -d <branch>

    // force delete a not yet merged branch
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

    // revert commit
    // alternate safe option
    // reverts the change done in the specified commit
    git revert <commit_id>

> Note:
> - Both reset and revert serve the same purpose.
> - However, there is key difference in how both commands achieve the objective.
> - Reset discards and orphans the undesired commits.
> - Revert makes a new commit after making the necessary changes.
> - Hence, using revert is safer when multiple collaborators share the repository.
> - Reset should be used in non-collaborative repositories.


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
    git stash save -u <stash_name>
    git stash save --include-untracked <stash_name>

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
    // -u ensures the remote branch gets tracked
    git push -u origin <branch>

> Note:
> - `git push` is also used to push changes to remote repo.
> - If the remote branch is being tracked, need not mention branch name.


### Clone a remote repository:

    // makes a copy of the remote repo locally
    git clone <remote_repo_url>

    // to give a custom name to the local repo
    git clone <remote_repo_url> <repo_name>

> Note:
> - Use `git branch` to list all local branches.
> - Use `git branch -r` to list all remote branches.
> - Use `git branch -a` to list all branches(local + remote).


### Fetch from remote repository:

    // syncs remote repo with local repo
    // gets info like new commits, new branches
    // does not merge any changes from remote to local repo
    git fetch


### Merge in fetched changes:

    // merges the fetched changes of remote to local branch
    // should follow a git fetch command
    git merge origin/master

    // directly fetches and merges remote branch changes
    // fetch + merge
    git pull



### Checkout remote branches:

    // checkout a new branch from remote branch
    // sets up the remote branch for tracking
    // switches to the new branch
    git branch -b <new_branch> <remote_branch>
    git branch -b <new_branch> origin/branch


### Delete remote branch:

    // remove a branch from the remote repo
    // the branch can remain locally
    // useful when a feature branch is complete and merged
    // deletes both tracking and corresponding remote branches
    git push origin :<branch>

    // command support from v1.7.0+
    git push --delete origin <branch>

    // short notation support from v2.8.0+
    git push -d origin <branch>

> Note:
> - If a collaborator deletes a remote branch, the tracking branch still remains on others' local system.
> - Use `git remote prune origin` to clean the stale tracking branches from local system.
> - `git remote prune origin --dry-run` shows what branches would be pruned.
> - A `git fetch` does not clean the stale tracking branches automatically.
> - Shortcut: prune, then fetch - `git fetch --prune/-p`
> - Config to always prune before fetch: `git config --global fetch.prune true`


### Force push to remote:

    // done when difference between local and remote branches
    // discards the commits in remote branches, that are not present in local
    git push -f
    git push --force
    
> Note:
> - Reasons to Force Push:
>   - Local version is better than remote version.
>   - Remote version went wrong and needs repair.
>   - Versions have diverged and merging is undesirable.
> - The other collaborators need to do a hard reset `git reset --hard origin/master` after a force push.


## Tags:

- Tags are named reference to a commit.
- Most often used to mark releases or special points in history.
- Two types of tags:
  - lightweight tags
  - annotated tags


### Create Tags:

    // add a lightweight tag
    git tag <tag> <commit_id>
    git tag issue136 655da716e7
    
    // annotated tag (most common)
    // can add one line or multi-line message
    git tag -a <tag> -m <message> <commit_id>
    git tag -a v1.1 -m "version 1.0" dd5c49428a0
    git tag -a -m "version 2.0" v2.0 94857bb4fc6
    
    // alternate way to create annotated tags
    git tag -am <message> <tag> <commit_id>
    git tag -am "version 1.0" v1.1 dd5c49428a0


### List tags:

    // list all tags
    git tag --list
    git tag -l

    // filter and list tags
    git tag -l "filter_string"

    // list all tags beginning with "v2"
    git tag -l "v2*"

    // list tags with annotations
    git tag -l -n
    git tag -ln
    

### Delete tags:

    // deletes a local tag
    git tag --delete <tag>
    git tag -d <tag>


### Push tags to remote:

- Tags are local unless shared to a remote.
- `git push` does not transfer tags.
- Tags must be explicitly transferred.
- `git fetch` automatically retrieves shared tags.

        // push a tag to remote
        git push origin <tag>

        // push all tags to remote
        git push origin --tags

        // fetch only tags (with necessary commits)
        // rarely used
        git fetch --tags

        // use push to delete a remote tag
        // similar to deleting a remote branch
        git push origin :<tag>
        git push --delete origin <tag>
        git push -d origin <tag>


### Checkout tags:

- Tags are not branches.
- Tags can be checked out, just like any commit.
  
        // optimal way to checkout a tag
        // create a branch from the tag
        git checkout -b <new_branch> <tag>


> Note:
> - It's also possible to directly checkout a tag using `git checkout <tag>`.
> - This leads to a state known as **Detached HEAD State**:
>   - Checking out a commit puts the local repo in a detached HEAD state.
>   - It's like being on an unnamed branch.
>   - New commits will not belong to any branch.
>   - Detached commits will be garbage collected (~ 2 weeks).
>   - There are 3 ways to save the orphaned commits:
>       - Tag the commit (HEAD detached): `git tag temp`
>       - Create a branch (HEAD detached): `git branch temp_branch`
>       - Create a branch and reattach HEAD: `git checkout -b temp_branch`
>   - To simply get out of the detached HEAD state, switch to any branch: `git checkout master`


## Cherry-pick:

- Apply the changes from one or more existing commits.
- Each **cherry-picked** commit is recorded as a new commit on the current branch.
- Conceptually similar to copy-paste.
- New commits will have different SHAs.


### Cherry-picking Commits:

    // cherry-pick a specific commit
    git cherry-pick <commit_id>

    // cherry-pick a range of commits
    git cherry-pick <start_commit_id>..<end_commit_id>

> Note:
> - Cannot cherry-pick a merge commit.
> - By default, the same commit message wil be used.
> - The original commit message can be modified using --edit or -e flag followed by the new commit message.
> - Can result in conflicts which must be resolved.


### Cherry-picking conflicts:

- Can abort cherry-picking in case of conflict.
- Can resolve the conflicts and continue with cherry-picking.

        // abort cherry-picking
        git cherry-pick --abort

        // continue after resolving conflicts
        git cherry-pick --continue

> Note:
> - Cherry-picking will automatically be paused in case of conflicts.
> - After resolving the conflicts, `git add` is to be used to mark resolution.
> - Only after resolution is marked, use command `git cherry-pick --continue`


## Diff Patches:

- Share changes via files.
- Useful when changes are not ready for a public branch.
- Useful when collaborators do not share a remote.
- Often used in discussions, reviews or approval processes.
  

### Create diff patches:

    // create a diff patch file
    git diff <commit_id_1> <commit_id_2> > <file_name.diff>

> Note:
> - Let there be three successive commits:
>   - commit-3 (latest / HEAD)
>   - commit-2
>   - commit-1 (oldest)
> - If we want commit-3 and commit-2 to be in a diff patch, command will be:
>   - `git diff commit1 commit3 > output.diff`


### Apply diff patches:

- Apply changes in a diff patch file to the working directory.
- Makes changes, but not commits.
- No commit history transferred.

        // apply a diff patch file
        git apply <path/file_name.diff>

> Note:
> - A patch cannot be applied to any working directory.
> - The current state of the working directory is a deciding factor in the applicability of a patch.


### Create formatted patches:

- Export each commit in Unix mailbox format.
- Useful for email distribution of changes.
- Is a regular diff file including commit messages.
- One commit per file by default.

        // export a single commit
        git format-patch -1 <commit_id>

        // export range of commits as formatted patch
        git format-patch <commit_id_1>..<commit_id_2>

        // scenario: export all commits on current branch which are not in master branch
        // by default considers blank as HEAD
        git format-patch master

        // put patch files into a directory
        // creates the directory if not present
        git format-patch master -o <directory_name>

        // output patches as a single file
        git format-patch <commit_id_start>..<commit_id_end> --stdout > <filename.patch>
        

### Apply formatted patches:

- Extract author, commit message, and changes from a mailbox message and apply them to the current branch.
- Similar to cherry-picking: same changes, different SHAs.
- Unlike diff patch, commit history is transferred.

        // apply single patch
        // am: apply mailbox patch
        git am <filename.patch>

        // apply all patches in a directory
        git am <directory>/*.patch


## Rebase:

- Take commits from a branch and replay them at the end of another branch.
- Useful to integrate recent commits without merging.
- Maintains a cleaner, more linear project history.
- Ensures topic branch commits apply cleanly.

> Note:
>
> - ### The Golden Rule of Rebasing: Thou shalt not rebase a public branch.
>   - Rebase abandons existing, shared commits and creates new, similar commits instead. 
>   - Collaborators would see the project history vanish.
>   - Getting all collaborators back in sync can be a nightmare.
>
> - ### How to Choose - Merge or Rebase?
>   - **Merge** to allow commits to stand out or to be clearly grouped.
>   - **Merge** to bring large topic branches back into master.
>   - **Rebase** to add minor commits in master to a topic branch.
>   - **Rebase** to move commits from one branch to another.
>   - **Merge** anytime the topic branch is already public and being used by others. **(The Golden Rule of Rebasing)**
> 
> - ### Merge vs Rebase
>
> |                    Merge                    |                         Rebase                         |
> | :------------------------------------------ | :----------------------------------------------------- |
> | Adds a merge commit.                        | No additional merge commit.                            |
> | Nondestructive.                             | Destructive: SHA changes, commits are rewritten.       |
> | Complete record of what happened and when.  | No longer a complete record of what happened and when. |
> | Easy to undo.                               | Tricky to undo.                                        |
> | Logs can become cluttered, non-linear.      | Logs are cleaner, more linear.                         |


### Rebase onto parent(master) branch:

    // rebase current branch to tip of master
    git rebase master

    // rebase speicifc branch to tip of master
    git rebase master <branch_name>

> Note:
> - Two very useful commands while rebasing:
>   - Useful for visualizing branches: `git log --graph --all --decorate --oneline`
>   - Return commit where specific branch diverges: `git merge-base master <branch_name>`


### Rebase conflicts:

 - Rebasing creates new commits on existing code.
 - May conflict with existing code.
 - Git pauses rebase before each conflicting commit, waiting for it to be resolved before proceeding with other commits.
 - Similar to resolving merge conflicts.
 - Unlike merge, after resolving commits, `git rebase --continue` is used instead of `git commit`.
 - Before using `git rebase --continue`, make sure the conflicts are also marked resolved using `git add <conflicted_file>`.
 - In order to skip a conflicting commit, use `git rebase --skip` to move on to other commits.
 - Rebasing can also be stopped by using `git rebase --abort`.


### Rebase onto other branches:

- Has three parameters:
  - newbase
  - upstream
  - branch
- The command specifies to gather commits from the <branch> branch upto the point where <branch> diverges from <upstream> branch and rebase the commits on <newbase> branch.


        // syntax
        git rebase --onto <newbase> <upstream> <branch>
        git rebase --onto master ui ui_rework


### Undo a rebase:

- Can undo simple rebases.
- Rebase is destructive.
- SHAs, commit messages, change sets can be altered.
- Undoing complex rebases may lose data.

        // undo, unless ORIG_HEAD has changed again
        git reset --hard ORIG_HEAD

        // undo by rebasing to former merge-base SHA
        git rebase --onto 9291f0c88 master new_feature

### Interactive rebasing:

- Chance to modify commits as they are being replayed.
- Opens the git-rebase-todo file for editing.
- Can reorder or skip commits.
- Can edit commit contents.

        //interactive rebase
        git rebase -i master new_feature

> Note:
> - Interactive rebase choices:
>    - pick, drop
>    - reword, edit
>    - squash, fixup
>    - exec 
> - Squash Commits:
>   - Fold two or more commits into one
>   - squash: combine change sets, concatenate messages
>   - fixup: combine change sets, discards commit message
>   - uses first author in the author series

### Pull rebase:

- Fetch from remote, then rebase instead of merging.
- Keeps history cleaner by reducing merge commits.
- Only use on local commits, that have not been shared to remote.
    