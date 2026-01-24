# Write a Docker File

## Task

- As per recent requirements shared by the Nautilus application development team, they need custom images created for one of their projects. Several of the initial testing requirements are already been shared with DevOps team. Therefore, create a docker file /opt/docker/Dockerfile (please keep D capital of Dockerfile) on App server 3 in Stratos DC and configure to build an image with the following requirements:

- a. Use ubuntu:24.04 as the base image.

- b. Install apache2 and configure it to work on 6100 port. (do not update any other Apache configuration settings like document root etc).

## Solution

### ssh into the app server

- ssh banner@stapp03

### Create a Dockerfile in /opt/docker

- sudo vi /opt/docker/Dockerfile

### Populate with this content

~
FROM ubuntu:24.04

RUN apt update && apt install -y apache2

RUN sed -i 's/Listen 80/Listen 6100/g' /etc/apache2/ports.conf

EXPOSE 6100

CMD ["apache2ctl", "-D", "FOREGROUND"]
~
