# Persisting Data

## Mounting Data

To mount local files to container:

`docker container run --volume [local directory] : [container directory]`

ex.
`docker container run --volume /Desktop/nginx/html:/var/www/html:ro -p 8080:80 subratabauri/nginx:latest`


## Shortening the Command for mount volume

** before ** `docker container run -v /some/extremely_long/directory/path/myfile.html : /var/www/html:ro -p 80:80 nginx:latest`

** after ** `docker container run -v $(pwd)/myfile.html : /var/www/html:ro -p 80:80 nginx:latest # after`

`Note:` This trick varies with operating systems.


## The Mount Option

`docker container run --mount type=bind,src="$(pwd)/html/",destination=/var/www/html,readonly -p 8080:80 subratabauri/nginx:latest`


## Volumes

`docker container run -it --volume /data [image]:[tag]`

ex. `docker container run -it --volume /data alpine:latest`

View all volumes with `docker volume ls`


## Naming Volumes

`docker container run -it --volume [name]:/data [image]:[tag]`

After deleting a container the volumes remain secure and can still be accessed and loaded into new containers. This is an effective way to preserve the state of your containers.

## Using Mount for Volumes
`docker container run --mount type=volume,src=[volume name],destination=/data,readonly [image]:[tag]`

Make it anonymous volume by ommitting the source

`docker container run --mount destination=/data,readonly [image]:[tag]`

or

`docker container run --mount dst=/data,readonly [image]:[tag]`


## Managing Volumes

**Remove unused volume:** `docker volume rm [volume name]`

**View volume details:** `docker volume inspect [volume name]`

Inspect a container with `docker container inspect [container name]` to find any mounted volumes under "Mounts"

To quickly remove all unused volumes: `docker volume prune`


## Disappearing Volumes

`docker container run --rm -v /data [image]:[tag]`

**Note:** This only works for anonymous volumes. If you provide a name, it will not be deleted.

## The VOLUMES Instruction

A volume can also be automatically created by a Dockerfile with the VOLUME instruction: 

`VOLUME /var/lib/postgresql/data`


## Simultaneous Access - Lab
### Access volumes from multiple containers
- Create a named volume
- Start an alpine container
  - Execute a shell
  - Mount the volume to /data
  - reate a file in /data (`touch data/test.file`)
- Start a seond alpine container
  - Execute a shell
  - mount the SAME volume


