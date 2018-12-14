# Git notes

Directed Acyclic Graph
*	One direction
*	Can’t point backwards

Commit ID – SHA1 hash of commit – First 7 chars are normally only important
Commit:
* Stores a snapshot of entire repo - intelligently

Structure:
* Trees - directories
* Blobs – files
  * Commit points to root of tree and that points to blobs
  * If the hash of the file is the same, don’t need to store again

## Branch

* Entire repo
* Pointer into the graph
* In Git speak – branch is a HEAD 

Create new branch
```
git checkout -b [name_of_your_new_branch]
```

Update to a branch
```
git checkout [branch name]
```

Push the branch to remote
```
git push origin [name_of_your_new_branch]
```

Show remotes
```
git branch –r
```

Print the name of the upstream branch
```
git branch –vv 
```

Merge – creates a commit with 2 par
Rebase - Instead of merging, which creates new commit with 2 parents – just replay changes on top of common ancestor
* Difficult when there are big differences between branches
* Creates a patch file
* Avoid deatached head state ```git rebase –abort```

Fast forward
* Git just updates the pointers if a straight line – no divergence

Detached Head
INDEX (Synonyms: stage or cache) 
* This is what’s going to be your next commit – snapshot (entire repo)
```git ls-files –stage```

Show what’s stored inside the INDEX for each file
```git ls-files –debug```

Git opens working dirand check if the time stamp or size has changed – doesn’t need to do complete diff, so fast
```git add ``` Do it often, can recover these

## Commands
```bash
git log –graph
git log –oneline
git log –graph –oneline – decorate
```
Create an alias for a nicer looking log:
```bash
git config --global alias.lol "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

```Git fetch``` gets the latest from the cloned repo, but doesn’t update HEAD. SAFE to do as often as you want
```Git pull``` gets the latest from the cloned repo and update HEAD: git fetch + git pull

git show <first 7 chars of ID>
*	Shows just the diff, but entire snapshot is stored
*	Computes the diff everytime
```
git cat-file 
git cat-file blob <xxxxxxx>
git reset –hard xxxxxxx
git diff HEAD—HEAD~1
```

Git stash – save changes, then you can come back to later

## Git Submodule
Repo within a repo. Allows you to ensure that a particular version of a dependent repo is used only.
Parent repo only knows that something has changed and tracks HEAD of subrepo.

To clone a repo which has subrepos: 
```
git clone ssh://git@gitlab.bt.local:2224/server/sensor-manager.git --recursive-modules
```

If the repo has already cloned, run: ```git submodule update --init –recursive```
To update: ```git submodule update```
