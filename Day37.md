# Copy file to Docker container

- Task: Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /opt/. Ensure the file is not modified during this operation.

## Confirming running containers

- docker ps

## Copying from host to docker container

- docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/opt/

## Validate file successfully copied

- sudo docker exec ubuntu_latest ls -l /opt/
