# Clone Git Repository on Storage Server

## Question

```bash

The DevOps team established a new Git repository last week, which remains unused at present. However, the Nautilus application development team now requires a copy of this repository on the Storage Server in the Stratos DC. Follow the provided details to clone the repository:



The repository to be cloned is located at /opt/games.git


Clone this Git repository to the /usr/src/kodekloudrepos directory. Perform this task using the natasha user, and ensure that no modifications are made to the repository or existing directories, such as changing permissions or making unauthorized alterations.
```

## Solution

### SSH into the storage server

- ssh natasha@ststor01

### switch user

- sudo su - natasha

### change directory

- cd /usr/src/kodekloudrepos

### Clone into the directory

- git clone /opt/games.git

