# Persisting Data

## Mounting Data

To mount local files to container:

`docker container run --volume [local directory] : [container directory]`

ex.
`docker container run --volume /Desktop/nginx/html:/var/www/html:ro -p 8080:80 subratabauri/nginx:latest`


## Shortening the Command for mount volume

**before** `docker container run -v /some/extremely_long/directory/path/myfile.html : /var/www/html:ro -p 80:80 nginx:latest`

**after** `docker container run -v $(pwd)/myfile.html : /var/www/html:ro -p 80:80 nginx:latest # after`

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


## Simultaneous Access - LAB
### Access volumes from multiple containers
- Create a named volume
- Start an alpine container
  - Execute a shell
  - Mount the volume to /data
  - Create a file in /data (`touch data/test.file`)
- Start a seond alpine container
  - Execute a shell
  - mount the SAME volume

#### We can share same volume amongst containers:

`docker volume create my-volume`

`docker container run --volume my-volume:/data alpine:latest sh`


## Using Volumes from Other Containers

`docker container run -it --name c1 -v test-data:/data alpine:latest sh`

**Copy volume from another container =>** `docker container run --volumes-from c1 -it alpine:latest sh`


## Prepopulating Volumes - LAB
### Mount a volume containing files
- Create a named volume test-data
  - Start a sh in a container running alpine
    - Mount the volume test-data to /data
- Create some files and folders in the volume
  - `touch /data/test.file`
  - `mkdir /data/some_dir`
- Stop the container running alpine
- Start the bash shell in a container running your nginx image
  Mount the volume test-data to /var/www/html
- What can you find in the directory /var/www/html?

### Mount a new volume
- Start the bash shell in a container running your nginx image
  - Mount a new named or anonymous volume to /var/www/html
- What can you find in the directory /var/www/html?


## When to Use Bind mount and Volumes
### Bind mounts

- When we want to access data from the host and the container source code and configuration files

### Volume

- When we want to persist data from the container
- When we want to share data between containers.

`df -h` **to check mounted volumes inside container**
