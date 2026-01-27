# Docker Ports Mapping

## Task 1: Pull nginx:alpine docker image on Application Server 3

- ssh user@stapp03

- docker pull nginx:alpine

## Task 2: Create a container named games using the image you pulled

- This is linked to using the `--name` in docker run in `Task 3`

## Task 3: Map host port 3000 to container port 80. Please keep the container in running state

- docker run -d --name games -p 3000:80 nginx:alpine
