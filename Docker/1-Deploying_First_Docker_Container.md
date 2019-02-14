# Docker Essentials

### Find existing images
`docker search <name>`

### Start a container based on a Docker Image
`docker run <options> <image-name>`

ex. `docker run -d redis`

By default, Docker will run a command in the foreground. To run in the background, the option -d needs to be specified.

### Lists all running containers
`docker ps`

### Provides more details about a running container, such as IP address
`docker inspect <friendly-name|container-id>`

### Display messages the container has written to standard error or standard out
`docker logs <friendly-name|container-id>`

### Port mapping
Ports are bound when containers are started using `-p <host-port>:<container-port>` option

ex. `docker run -d --name redisHostPort -p 6379:6379 redis:latest`

#### Expose on a randomly available port
ex. `docker run -d --name redisDynamic -p 6379 redis:latest`

#### To check which port has been assigned
ex. `docker port redisDynamic 6379`

### Persisting Data
Docker Hub [documentation for Redis](https://hub.docker.com/_/redis/) shows that the official Redis image stores logs and data into a /data directory.
Any data which needs to be saved on the Docker Host, and not inside containers, should be stored in /opt/docker/data/redis
ex. `docker run -d --name redisMapped -v /opt/docker/data/redis:/data redis`

## Protip
Docker allows to use $PWD as a placeholder for the current directory.

## Running A Container In The Foreground
The command `docker run ubuntu ps` launches an Ubuntu container and executes the command ps to view all the processes running in a container.

Using `docker run -it ubuntu bash` allows Jane to get access to a bash shell inside of a container.
