# Git useful commands

### Initialize a git repository
```
git init
```

### Add files/files to the stage
```
git add .
```
or
```
git add <singleFilename>
```

### Commit a change
```
git commit -m "Message"
```

### View the log of commits
```
git log
```

### View the log of commits with the diff
```
git log -p
```

### View the difference of files (not added and not staged)
```
git diff
```

### Discard changes in the WD (local)
```
git checkout -- <filename>
```

### Reset a modified file (staged)
``` sh
git reset HEAD <filename>
# can do: git checkout -- <filename>
```

### View log only one line per commit showing
``` sh
git log --oneline
# --decorate (view pointers i.e. HEAD)
# --graph (view branching)
```

###  Move to certain commit and discard the subsequents (keeping the changes unstaged)
``` sh
# WARNING! Destructive commit
git reset <commit>
# then can handle the unstaged changes i.e. "git checkout -- <filename>"
```

###  Move to certain commit and discard the subsequents (discard local changes)
``` sh
# WARNING! Destructive commit
git reset --hard <commit>
```

###  Move to certain commit and discard the subsequents (keeping the changes in the stage)
``` sh
# WARNING! Destructive commit
git reset --soft <commit>
```

###  Revert the changes safely (keeping the changes as new commit)
``` sh
git revert <commit> # can be HEAD~x
```

###  Revert the changes safely (keeping the changes in stage)
``` sh
git revert --no-commit <commit> # can be HEAD~x
# then: git revert --continue to end the reversion with a commit
```

###  Simple merge of two branches
``` sh
git ckeckout <destinyBranch> # i.e. master
git merge <originBranch> # i.e. develop
```

###  Abort the merge
``` sh
git merge --abort
```

### Tag the last commit (actual commit)
``` sh
git tag <tagID> # i.e. "v1.1.0"
```

### Tag a specific commit
``` sh
git tag <tagID> <commitHash>
```

### Pull the repository ordering the commits local and remote to avoid an extra commit
``` sh
git pull --rebase <origin> <branch>
# i.e. (the most usual)
# git pull --rebase origin master
```

### Work in other branch and set as the master (discarding the actual master)
``` sh
# Warning! Destructive
git branch <branch_name>    # i.e. git branch new_master
git checkout <branch>  # i.e. git checkout new_master

# this two ^ can be simplified in one command
git checkout -b <branch_name>   # i.e. git checkout -b new_master
#
git branch -D <master>
git branch -mv <Checkouted_branch> <new_branch_name> # i.e. git branch -mv new_master master
```

### Untrack but keep the file
``` sh
git update-index --assume-unchanged FILE_NAME
```

### Track a file ignored by the previous command
``` sh
git update-index --no-assume-unchanged FILE_NAME
```
