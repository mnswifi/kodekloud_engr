# Git Revert Some Changes

## Questions

```bash
The Nautilus application development team was working on a git repository /usr/src/kodekloudrepos/apps present on Storage server in Stratos DC. However, they reported an issue with the recent commits being pushed to this repo. They have asked the DevOps team to revert repo HEAD to last commit. Below are more details about the task:


In /usr/src/kodekloudrepos/apps git repository, revert the latest commit ( HEAD ) to the previous commit (JFYI the previous commit hash should be with initial commit message ).


Use revert apps message (please use all small letters for commit message) for the new revert commit.

```


## Solutions 

### SSH into the storage server

- ssh natasha@ststor02

### Change directory to `/usr/src/kodekloudrepos/games`

- cd /usr/src/kodekloudrepos/apps

### Check commits

- git log --oneline

### Revert commit 

- git revert -n HEAD 

- git commit -m "revert apps"

Or 

- git revert HEAD --no-edit

- git commit --amend -m "revert apps"
