# Git Create Branches

## Question

```bash
Nautilus developers are actively working on one of the project repositories, /usr/src/kodekloudrepos/demo. Recently, they decided to implement some new features in the application, and they want to maintain those new changes in a separate branch. Below are the requirements that have been shared with the DevOps team:



On Storage server in Stratos DC create a new branch xfusioncorp_demo from master branch in /usr/src/kodekloudrepos/demo git repo.


Please do not try to make any changes in the code.

```

## Solutions

### change directory to `/usr/src/kodekloudrepos/demo`

- cd /usr/src/kodekloudrepos/demo

### change branch

- sudo git config --global --add safe.directory /usr/src/kodekloudrepos/demo

- sudo git branch checkout master

### create branch 

- sudo git branch xfusioncorp_demo

