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
| `git pull <origin> <branch>` | Update local repo with the missing commits on the remote repo (using `<origin>` connection on <branch> branch) |
| `git add <file>` | Add file changes to stage/cache area |
| `git commit -m 'Commit message'` | Apply changes to local repo with a message |
| `git push <origin> <branch>` | Upload the changes to reporte repo (using `<origin>` connection on `<branch>` branch) |
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
| `git stash save 'name'` | Stash the changes in a dirty working directory away but with a `<name>` as ID |
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

### Manual or man
Use command `man` to read all the information regarding any command in the system.
Every single binary has its own entry in the manual, even the ones from external packages.
> `man <command_name>` will print out an entry for that command, listing all the arguments and explaining each one of them.


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
| `mkdir <FOLDER_NAME>` | Create a folder |
| `cp <FILE_OR_FOLDER> <NEW_DESTINATION>` | Copy a file or folder |
| `mv <FILE_OR_FOLDER> <NEW_DESTINATION>` | Move a file or folder |
| `mv <FILE_OR_FOLDER_OLD> FILE_OR_FOLDER_NEW>` | Change file or folder name |
| `rm <FILE>` | Remove a file. *Warning*: there is no trash bin in Linux when using the command line |
| `rm -r <DIRECTORY>` | Remove recursively, used to delete an entire directory. |
| `rmdir <DIRECTORY>` | Remove an empty directory |

### Permissions and ownership
All files have the following attributes:
- Owner permissions: the owner's permissions determine what actions the owner of the file can perform on the file.
-	Group permissions: the group's permissions determine what actions a user, who is a member of the group that a file belongs to, can perform to a file.
-	Other permissions: the permissions for all other users.

```bash
  > ls -l
  drwxrwxrwx [...]
```

By taking a look at the first 10 characters, we can see that this directory has full permissions:
- `d`: indicates that the file is a directory.
- `rwx`: read, write and execution permission for Owner
- `rwx`: read, write and execution permission for Group
- `rwx`: read, write and execution permission for Other

#### Representing permissions
To represent these three characters for a single attribute we use only one number, a permission byte.

Depending on the type of file permissions that we want to assign, we will just add the numbers, when adding permissions we need to use a number for each attribute (owner, group and other). 

| Value | Description | Permission |
| :--- | :--- | :--- |
| `0` | No permission | `---` |
| `1` | Execute | `--x` |
| `2` | Write | `-w-` |
| `4` | Read | `r--` |
| `3` | Execute and Write | `-wx` |
| `5` | Execute and Read | `r-x` |
| `6` | Read and Write  | `rw-` |
| `7` | Read, Write and Execute | `rwx` |

#### Commands
| Command | Description |
| :--- | :--- |
| `chmod <owner permissions><group permissions><other permission> <FILE>` | Change mode. Modify permissions. eg: `chmod 777 file` |
| `chown <user_name>:<group_name>` | Change file owner |

### SUDO command
| Command | Description |
| :--- | :--- |
| `sudo <command>` | "Super user do". Used to execute commands as root (System Owner) as a way to temporarily grant a user administrative rights. `root` user password requiered prior command execution. |

### Space management commands
| Command | Description |
| :--- | :--- |
| `df` | Display Filesystem and disk utilization |
| `df -h` | Display in "human readable" format |
| `du <optional_dir_or_file>` | Disk Usage. Used to check the space usage of one or various files on a directory |
| `du -h ` | Display in "human readable" format |
| `du -a` | List all files on the directory (CANNOT USE -a AND -s) |
| `du -s` | Summarize the output (the sum of all the space usage) (CANNOT USE -a AND -s) |

#### du command examples
| Command | Output |
| :--- | :--- |
| `du -ah` | Print all files in directory in a "human readable" format |
| `du -sh *` | Print each file/directory disk usage in a "human readable" format (**MOST USED**) |
| `du -sh <file_name>` | Print disk usage for a file or directory |

### File content management
| Command | Description |
| :--- | :--- |
| `more <file>` | Read text files. Controls [below](#more-command-controls) |
| `tail <file>` | Print the last lines of a file |
| `head <file>` | Print the top lines of a file |
| `cat <file>` | Print all file content |
| `\|` | "Pipe". Allow the use of two or more commands using the output of the left command as input for the right one. |
| `grep` | Used in combination with "Pipe" (|) to search for a specific string in a file or directory. Example:  |
| `grep -e` | `-e` argument allow us to add more than one term for searching |

#### more command controls
-	`enter` key: scroll down line by line
-	`space bar`: next page
-	`b`: go back one page
-	`q`: quit

#### grep command examples
If I want to seach for error (ERR) or warning (WARN) messages:
```bash
  > cat log | grep -e ERR -e WARN
  ERR: ....
  ERR: ....
  WARN: ....
```

### Vi / Vim
| Command | Description |
| :--- | :--- |
| `` |  |


### Process listing and handling
| Command | Description |
| :--- | :--- |
| `ps -ef` | Print all processes with their ids. Also prints owners and groups |
| `kill -9 <pid>` | Kill locked process using process id |
| `ps -ef \| grep <process_name>` | Search for a specific process |

### JAVA files
| Command | Description |
| :--- | :--- |
| `java -jar <FILE_NAME.jar>` | Run a JAVA '.jar' file |
| `java -agentlib:jdwp=transport=dt_socket,server=y,suspend=y,address=5005 -jar <FILE_NAME.jar>` | Debug a JAVA '.jar' file (IDE needed) |

#### Debug command for .jar files
1. `JDWP`: Java Debug Wire Protocol
1. `transport=dt_socket`: specifies the transport mechanism to use for the JDWP connection. In this case, it's using a socket-based transport.
1. `server=y`: indicates that the JVM should act as a server for the JDWP connection, meaning that it will listen for a debugger to connect.
1. `suspend=y`: determines whether the JVM should wait for a debugger to connect before running the program. If `suspend=y`, then the program will start up but wait for a debugger to connect before it starts running. If `suspend=n`, then the program will start running immediately after the JVM starts up.
1. `address=5005`: specifies the port number to use for the JDWP connection. In this case, it's using port 5005. The debugger will use this port to connect to the JVM and control the execution of the program.

> This option tells the JVM to listen on port 5005 for a socket-based JDWP connection from a debugger, and to start running the program immediately without waiting for a debugger to connect.

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
