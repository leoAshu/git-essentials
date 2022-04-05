# Git Essentials

### Git is a Version Control System(VCS), aka Source Code Management(SCM).

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

- Git uses **Three Tree Architecture** as opposed to other VCSs that use traditional **Three Tree Architecture**

Two Tree Architecture - Traditional        |  Three Tree Architecture - Git
:-----------------------------------------:|:-----------------------------------------:
![](images/two-tree-architecture.png)      |  ![](images/three-tier-architecture.png)

<br>

## Git Workflow:

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

## Commonly Used Commands:

#### Set configuration:
    git config --global <config_name> <value>

    git config --global user.name "Ashutosh Ojha"

    git config --global user.email "ashutosh.ojha2009@gmail.com"

    git config --global core.editor "atom --wait"
    
    git config --global color.ui true

<br>

#### Show configuration:
    // lists all config properties
    git config --list

    // shows a specific configuration property
    git config <config_property>

    // shows a user name
    git config user.name

<br>

#### Show command manual:
    git help <command_name>

    man git-<command_name>

<br>

#### Initialize repository:
    // adds .git to directory
    // converts a normal directory into a repository
    git init 

<br>

#### Stage changes:
    git add <change_path>

    // stages all changed files in the directory
    git add .

    // stages a specific change
    git add changed_file.txt 

<br>

#### Commit changes:
    // makes the staged changes permanent and tracks them
    git commit

    // commit with a message
    git commit -m "<message>"

    // commit with a message and additional descriptions
    git commit -m "<message>" "<desc1>" "<desc2>"

<br>

#### View commit log:
    // lists all the commits
    git log

    // limits the number of commits to be shown
    git log -n <limit>

    // filter by date
    git log --since=<date1> --until=<date2>
    
    // filter by author name
    git log --author="<author_name>"

    // filter by commit message
    git log --grep="<commit_message>"

<br>
