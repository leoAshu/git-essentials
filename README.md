# Git Essentials

#### Git is a Version Control System(VCS), aka Source Code Management(SCM).

#### Previous VCS Tools:

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

### Github:
- 2008
- hosts Git repositories
- purchased by Microsoft in 2018

### Distributed Version Control:
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

### Git Configuration:

1. System Config File-
    - Scope:        `git config --system`
    - Win Path:     `Program Files\Git\etc\gitconfig`
    - Mac Path:     `etc\gitconfig`

2. User Config File-
    - Scope:        `git config --global`
    - Win Path:     `Users\<user_name>\.gitconfig`
    - Mac Path:     `$Home\.gitconfig`

3. Project Config File-
    - Scope:        `git config`
    - Path:         `my_project\.git\config`

### Commands:

1. Set configuration:
    - `git config --global <config_name> <value>`
    - To set the user name:        `git config --global user.name "Ashutosh Ojha"`
    - To set the user email:       `git config --global user.email "ashutosh.ojha2009@gmail.com"`
    - To set the default editor:   `git config --global core.editor "atom --wait"`
    - To enable colored ui:        `git config --global color.ui true`

2. Show configuration:
    - To list all the config properties:   `git config --list`
    - To show a specific config_property:  `git config <config_property>`
    - To show the user name:               `git config user.name`

2. Show command manual:
    - `git help <command_name>`
    - `man git-<command_name>`

3. Initialize repository:
    - To turn a directory into a git repository: `git init`
    - Adds a .git file to the root directory

4. Stage or add changes:
    - `git add <change_path>`
    - To add all changes:      `git add .`
    - To add a changed file:   `git add <changed_file_path>`
    - The changes are not tracked/made permanent yet

5. Commit changes:
    - `git commit`
    - To commit with a message:    `git commit -m "<message>"`
    - To add descriptions after a message: `git commit -m "<message>" "<desc1>" "<desc2>"`
    - Makes the staged changes permanent and tracks them
    - Commit messages should be in present tense
    - Can develop shorthands: "[css,js]", "bugfix:", etc.

3. View the commit log:
    - `git log`
    - To limit the number of commits shown: `git log -n <limit>`
    - To show commits after/before a date:  `git log --since/--until=<date>`
    - To filter commits by author:          `git log --author="<author_name>"`
    - To search commits by commit message:  `git log --grep="<commit_message>"`