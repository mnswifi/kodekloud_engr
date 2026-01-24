# Create a Docker Network

## Task

- The Nautilus DevOps team needs to set up several docker environments for different applications. One of the team members has been assigned a ticket where he has been asked to create some docker networks to be used later. Complete the task based on the following ticket description:

a. Create a docker network named as blog on App Server 1 in Stratos DC.

b. Configure it to use macvlan drivers.

c. Set it to use subnet 192.168.30.0/24 and iprange 192.168.30.0/24.

## Solution

### Login to the app server 1

- ssh tony@stapp01

### Create network with macvlan driver and required parameters

- docker network create -d macvlan --subnet=192.168.30.0/24 --ip-range=192.168.30.0/24 blog

### Validate creation

- docker network ls

- docker network inspect blog
