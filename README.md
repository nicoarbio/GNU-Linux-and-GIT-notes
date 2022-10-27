# GNU-Linux & GIT notes

Hey there! These are my notes for Linux and Git topics

##### Table of Contents
- [GNU-Linux & GIT notes](#gnu-linux--git-notes)
        - [Table of Contents](#table-of-contents)
  - [GIT](#git)
    - [git remote | git fetch | git push | git pull](#git-remote-|-git-fetch-|-git-push-|-git-pull)
    - [git add | git commit | git diff | git stash | .gitignore](#git-add-|-git-commit-|-git-diff-|-git-stash-|-.gitignore)
    - [Branches](#branches)
    - [Differences and Merging](#differences-and-merging)
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
| `git log` | Shows the commit logs |
| `git log --graph --decorate` | Shows the commit logs but pretty |
| `git pull <origin> <branch>` | Update local repo with the missing commits on the remote repo (using <origin> connection on <branch> branch) |
| `git add <file>` | Add file changes to stage/cache area |
| `git commit -m 'Commit message'` | Apply changes to local repo with a message |
| `git push <origin> <branch>` | Upload the changes to reporte repo (using <origin> connection on <branch> branch) |
| `git commit --amend -m 'New Commit message` | Modify the message of the last commit |

### Git Stash
| Command | Description |
| :--- | :--- |
| `git stash` | Stash the changes in a dirty working directory away |
| `git stash pop` | Takes back the stashed changes and deletes them from the stack |

#### Git Stash (but safety)
| Command | Description |
| :--- | :--- |
| `git stash list` | List the stash entries that you currently have |
| `git stash save 'name'` | Stash the changes in a dirty working directory away but with a <name> as ID |
| `git stash apply stash@{n}` | Behaves exactly like pop, but do not remove the state from the stash list. n is the index in the stack |
| `git stash drop stash@{n}` | Remove a single stash entry from the list of stash entries. n is the index in the stack |


### Branches
- Branches are like pointers for each version we want to build from our project.
- Each branch is an independent line(branch) of development. Then they can be merged!
- The master/main branch is initially created, and from it the rest of the branches are created
 
| Command | Description |
| :--- | :--- |
| `git branch` | Display actual branch |
| `git branch <new_branch>` | Create a new branch |
| `git branch -m <actual_branch_name> <new_name>` | Change name of a branch |
| `git checkout <branch>` | Changes current branch |
| `git branch -d <branch>` | Delete a branch (You must do a checkout to another branch before deleting) |

### Differences and Merging
| Command | Description |
| :--- | :--- |
| `git diff --cached <file>` | Shows the differences between file and the changes in stage area (cached == staged) |
| `git diff <branch_1> <branch_2>` | Display differences at level file between branches  |
| `git merge <branch_src> <branch_tgt>` | Merge source into target branches (always checkout target branch) |

## GNU-LINUX

### Some terminology
- ACL: Access Control Lists.
- APT: Advanced Package Tool. Debian based package management.
- YUM: Yellowdog Updater Manager. Red Hat based package management. Sooner will be replaced by `dnf`.
- MBR: Master Root Record. Partition schema table.
- GPT: GUID Partition Table. Better than MBR.
- LVM: Logical Volume Manager. Tools to create virtual partitions.

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
| `|` | Pipe |
| `grep` |  |
| `grep -e` |  |

### Vi / Vim
| Command | Description |
| :--- | :--- |
| `` |  |


### Process listing and handling
| Command | Description |
| :--- | :--- |
|  |  |

### JAVA files
| Command | Description |
| :--- | :--- |
| `java -jar FILE_NAME.jar` | Run a JAVA '.jar' file |

### Zipping and Compressing and Packaging
| Command | Description |
| :--- | :--- |
| `tar -cf <new .tar> <directory>` | Create a package with the files in the directory |
| `tar -tf <.tar>` | Displays content in .tar file |
| `` |  |
| `xz <file>` | Compress files and creates a *.xz file |
| `xz -d <file>` | Uncompress a *.xz file |
| `bzip2 <file>` | Compress files and creates a *.bz2 file |
| `bzip2 -d <file>` | Uncompress a *.bz2 file |
| `gzip <file>` | Compress files and creates a *.gz file |
| `gzip -d <file>` | Uncompress a *.gz file |
