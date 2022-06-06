# GNU-Linux & GIT notes

Hey there! These are my notes for Linux and Git topics

##### Table of Contents
- [GNU-Linux & GIT notes](#gnu-linux--git-notes)
        - [Table of Contents](#table-of-contents)
  - [GIT](#git)
  - [GNU-LINUX](#gnu-linux)
    - [Navigation through filesystem](#navigation-through-filesystem)
    - [Files and directories management](#files-and-directories-management)
    - [Permissions and ownership](#permissions-and-ownership)
    - [SUDO command](#sudo-command)
    - [Space management commands](#space-management-commands)
    - [File content management](#file-content-management)
    - [Process listing and handling](#process-listing-and-handling)
    - [JAVA files](#java-files)


## GIT

### git remote | git fetch | git push | git pull
https://www.atlassian.com/es/git/tutorials/syncing 

### git add | git commit | git diff | git stash | .gitignore
https://www.atlassian.com/es/git/tutorials/saving-changes/git-diff

| Command | Description |
| :--- | :--- |
| `git status` | Checks the actual status of the local repo |
| `git pull <origin> <branch>` | Update local repo with the missing commits on the remote repo (using <origin> connection on <branch> branch) |
| `git add <file>` | Add file changes to stage/cache area |
| `git commit -m 'Commit message'` | Apply changes to local repo with a message |
| `git push <origin> <branch>` | Upload the changes to reporte repo (using <origin> connection on <branch> branch) |
| `git diff --cached <file>` | Shows the differences between the local file and the local file in stage area (cached == staged) |

### Branches
Branches are like pointers for each version we want to build from our project.
Each branch is an independent line(branch) of development. Then they can be merged!
The master/main branch is initially created, and from it the rest of the branches are created
 
| Command | Description |
| :--- | :--- |
| `git branch` | Display actual branch |
| `git branch <new_branch>` | Create a new branch |
| `git branch -m <actual_branch_name> <new_name>` | Change name of a branch |
| `git checkout <branch>` | Changes current branch |
| `git branch -d <branch>` | Delete a branch (You must do a checkout to another branch before deleting) |


## GNU-LINUX

### Navigation through filesystem
| Command | Description |
| :--- | :--- |
| `clear` | Clear shell |
| `pwd` | Actual directory (print working directory) |
| `cd` | Change directory |
| `ls` | Display folders in the actual directory |
| `ls -r` | IDEM but reverse |
| `ls -l` | Display permissions, user owner, group, creation date, etc |
| `aptitude` |  |


### Files and directories management
| Command | Description |
| :--- | :--- |
| `mkdir FOLDER_NAME` | Create a folder |
| `cp FILE_OR_FOLDER NEW_DESTINATION` | Copy a file or folder |
| `mv FILE_OR_FOLDER_OLD FILE_OR_FOLDER_NEW` | Move a file or folder |
| `mv FILE_OR_FOLDER NEW_DESTINATION` | Change file or folder name |
| `rm FILE` | Remove a file. *Warning*: there is no trash bin in Linux when using the command line |
| `rm -r DIRECTORY` | Remove recursively, used to delete an entire directory. |
| `rmdir DIRECTORY` | Remove an empty directory |

### Permissions and ownership
| Command | Description |
| :--- | :--- |
| `chmod` |  |
| `chown` |  |

### SUDO command
| Command | Description |
| :--- | :--- |
| `sudo` |  |

### Space management commands
| Command | Description |
| :--- | :--- |
| `df` | Display Filesystem |
| `df -h` | Display Filesystem size in GigaBytes |
| `du -sh *` |  |

### File content management
| Command | Description |
| :--- | :--- |
| `more` |  |
| `|` |  |
| `grep` |  |
| `grep -e` |  |

### Process listing and handling
| Command | Description |
| :--- | :--- |
| `` |  |

### JAVA files
| Command | Description |
| :--- | :--- |
| `java -jar FILE_NAME.jar` | Run a JAVA '.jar' file |
