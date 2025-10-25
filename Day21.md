# Setup Git Repository on Storage Server

## Question 

```bash
The Nautilus development team has provided requirements to the DevOps team for a new application development project, specifically requesting the establishment of a Git repository. Follow the instructions below to create the Git repository on the Storage server in the Stratos DC: Utilize yum to install the git package on the Storage Server. Create a bare repository named /opt/media.git (ensure exact name usage).
```

### Login to storage server

- ssh user@storageserver

### Install git

- sudo yum install -y git

### create and initialize directory as bare

- sudo mkdir -p /opt/media.git
- cd /opt/media.git
- sudo git init --bare

### Example in Usage 

```bash

# On storage server (central repo)
sudo git init --bare /opt/media.git

# On developer machine (working repo)
git clone ssh://user@ststor01/opt/media.git
cd media
echo "Hello world" > index.html
git add index.html
git commit -m "Add homepage"
git push origin main

```