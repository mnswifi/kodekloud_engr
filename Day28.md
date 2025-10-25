# Git Cherry Pick

## Question

```bash
The Nautilus application development team has been working on a project repository /opt/news.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with the DevOps team:



There are two branches in this repository, master and feature. One of the developers is working on the feature branch and their work is still in progress, however they want to merge one of the commits from the feature branch to the master branch, the message for the commit that needs to be merged into master is Update info.txt. Accomplish this task for them, also remember to push your changes eventually.

```

## Solutions 

### SSH into the storage server

- ssh natasha@ststor02

### Change directory to `/usr/src/kodekloudrepos/news`

- cd /usr/src/kodekloudrepos/apps

### Check branches

- git branch -a

### Switch to master branch if not

- git checkout master

### Check commits

- git log feature --oneline

Look for commit message "info.txt" and copy the commit hash

### Cherry-pick specific commit into master

- git cherry-pick <commit hash>

### If there are merge conflicts

```bash
git add .
git cherry-pick --continue

```

### Verify the commit now appears

- git log --oneline

