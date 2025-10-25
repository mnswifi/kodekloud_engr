# Git merge branches

## Question 

```bash
The Nautilus application development team has been working on a project repository /opt/cluster.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. They recently shared the following requirements with DevOps team:



Create a new branch nautilus in /usr/src/kodekloudrepos/cluster repo from master and copy the /tmp/index.html file (present on storage server itself) into the repo. Further, add/commit this file in the new branch and merge back that branch into master branch. Finally, push the changes to the origin for both of the branches.

```

## Solutions

### SSH into the storage server

- ssh natasha@ststor02

### Change directory to `/usr/src/kodekloudrepos/cluster`

- cd /usr/src/kodekloudrepos/cluster

### check current status and branch

- git status

- git branch

### create and switch to `nautilus` branch

- sudo git branch -b nautilus

### copy `\tmp\index.html` into branch

- sudo cp -r \tmp\index.html .

### Add and commit

- sudo git add index.html

- sudo git commit -m "added index.html"

### Push to origin

- sudo git push --set-upstream origin nautilus

- sudo git push

### Switch back to `master` branch to merge

- sudo git checkout master

- sudo git pull

- sudo git merge nautilus

- sudo git add 

- sudo git commit 

- sudo git push
