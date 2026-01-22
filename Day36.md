# Deploy Nginx Container on Application Server

## SSH to the application Server

- ssh username@appserver

## Check docker status

- sudo systemctl status docker

## Enable and Start docker

- sudo systemctl enable docker
- sudo systemclt start docker

## Run this docker command to pull and lauch image

- docke run -d --name nginx_2 nginx:alpine

## Confirm image is in running state

- sudo docker inspect -f '{{.State.Status}}' nginx_2
