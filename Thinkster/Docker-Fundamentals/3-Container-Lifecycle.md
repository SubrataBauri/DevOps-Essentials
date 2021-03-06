# Container Lifecycle

## Detaching and Attaching

Start a container with a command like this one:
`docker conatiner run --name c1 -it alpine:latest sh`

`-it` allows you to easily detach the container later by pressing `ctrl+p+ctrl+q`. If you instead use `-itd` the container will initialize unattached.

You can re-attach to a running container by entering `docker container attach [container name]`


## Execute commands inside Container

To start a second program inside your container:
`docker container exec [container name] [command]`

To run a shell inside your container, run
`docker container exec -it [container name] sh`


## Interacting with Containers
Starting a container with the **-i** flag will show no prompt, but allow you to enter commands and return output.

The **-t** flag on its own shows a prompt but will not execute commands. It is responsible for creating the prompt and positioning your cursor.

It is good practice to use both flags.


## Stopping a Container

`docker container stop [container name]`

This command sends a `SIGTERM` command to terminate the container. If the container does not stop after a grace period, Docker will kill the process with `SIGKILL`.

You can kill a container instantly by calling:

`docker container kill [container name]`

`ctrl-c` will forward a `SIGINT` message to a running container, which forwards it to its process ID. It will only exit when that process has terminated. This may not be immediate.


## Running two commands together

`docker image build -t subratabauri/nginx:latest . && docker container run --name c1 --rm subratabauri/nginx:latest`


## Reading Logs

To view all logs for a running container:

`docker container logs [container name]`

Continuously update the log, run the same command with the `-f`:

`docker container logs -f [container name]`
