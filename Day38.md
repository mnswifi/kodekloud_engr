# Pull docker image

- Task: Pull busybox:musl image on App Server 1 in Stratos DC and re-tag (create new tag) this image as busybox:blog.

## Validate docker is up and running

- sudo systemctl status docker

## Pull busybox:musl

- sudo docker pull busybox:musl

## Tag busybox:musl to busybox:blog

- sudo docker tag busybox:musl busybox:blog
