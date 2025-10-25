# Git manage remote

## Question

```bash
The xFusionCorp development team added updates to the project that is maintained under /opt/games.git repo and cloned under /usr/src/kodekloudrepos/games. Recently some changes were made on Git server that is hosted on Storage server in Stratos DC. The DevOps team added some new Git remotes, so we need to update remote on /usr/src/kodekloudrepos/games repository as per details mentioned below:


a. In /usr/src/kodekloudrepos/games repo add a new remote dev_games and point it to /opt/xfusioncorp_games.git repository.


b. There is a file /tmp/index.html on same server; copy this file to the repo and add/commit to master branch.


c. Finally push master branch to this new remote origin.
```

## Solutions

### SSH into the storage server

- ssh natasha@ststor02

### Change directory to `/usr/src/kodekloudrepos/games`

- cd /usr/src/kodekloudrepos/cluster

### Add remote git server

- git remote add dev_games /opt/xfusioncorp_games.git

### Verify remote servers

- git remote -v

### Copy files in `/tmp/index.html` to current directory

- cp /tmp/index.html .

### Verify it exists

- ls -l

### Add and commit

- git add .

- git commit -m "Add index.html to master branch"

### Verify commit 

- git log --oneline -1

### Push master branch to the new remote

- git push dev_games master # This command pushes local master branch to the master branch on the dev_games remote (/opt/xfusioncorp_games.git)

### Verify push 

- git ls-remote dev_games
