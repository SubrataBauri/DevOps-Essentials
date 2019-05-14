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

