# Install Docker packages and Start Docker Service

## Remove old docker versions

sudo yum remove -y docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine

## Install required packages

sudo yum install -y yum-utils device-mapper-persistent-data lvm2

## Add docker repository

sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

## Install Docker

sudo yum install -y docker-ce docker-ce-cli containerd.io

## Start & enable Docker

sudo systemctl start docker
sudo systemctl enable docker

## Verify Docker

docker --version
sudo docker run hello-world
