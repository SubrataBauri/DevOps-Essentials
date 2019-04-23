## Running First Container
`docker container run hello-world`

## Starting a Shell
`docker container run -it alpine sh`

The `-it` flag tells Docker that you are running an interactive program. 
The `sh` command indicates that you are executing a command inside the container.

To stop the shell press `control + D`

## Finding Images
`docker container run -it [NAME-OF-IMAGE-HERE] shell`

## Letting Things Run
Each time you run the command `docker container run` a new container is created.

Pressing `control + D` quits a shell and terminates the container.

Pressing `control + P` and `control + Q` allows you to detach from a container without closing it. 

You can re-attach with the command `docker container attach [NAME-OF-CONTAINER]`.

The command `docker container ls -a` lists all containers, even those not running.

Containers can be restarted using the command `docker container start [NAME-OF-CONTAINER]`.

To stop a container use the command `docker container stop [NAME-OF-CONTAINER]`.

You can start a container in detached mode using the command `docker container run -itd [NAME-OF-CONTAINER] sh`.

## Removing Containers and Images
`docker container rm [ID-OF-CONTAINER]`

`docker container ls -aq`. The `-aq` flag specifies that all container IDs should be listed.

To delete all containers run the command `docker container rm $(docker container ls -aq)`

Delete individual images using `docker image rm [NAME-OF-IMAGE]`

## Hints
`docker container run --rm [NAME-OF-IMAGE-HERE]`, docker will automatically remove the container when it exits.

Sssign names yourself using the command `docker container run --name [NAME-OF-CONTAINER-HERE] [NAME-OF-IMAGE-HERE]`
