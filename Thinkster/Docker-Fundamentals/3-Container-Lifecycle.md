# Container Lifecycle

## Detaching and Attaching

Start a container with a command like this one:
`docker conatiner run --name c1 -it alpine:latest sh`

`-it` allows you to easily detach the container later by pressing `ctrl+p+ctrl+q`. If you instead use `-itd` the container will initialize unattached.

You can re-attach to a running container by entering `docker container attach [container name]`