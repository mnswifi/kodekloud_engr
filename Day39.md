# Create a Docker Image From Container

## Task

- Create an image beta:devops on Application Server 3 from a container ubuntu_latest that is running on same server.

## Solution

### login to app server 3

- ssh user@appserver3

### Validate running container

- docker ps
- docker commit ubuntu_latest beta:devops
- docker images | grep beta
