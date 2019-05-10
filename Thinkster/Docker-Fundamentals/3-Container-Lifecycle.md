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

