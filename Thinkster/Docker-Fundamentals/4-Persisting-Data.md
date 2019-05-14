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

`docker container run --mount type=bind,src="$(pwd)/html/",destination=/var/www/html,readonly -p 80:80 subratabauri/nginx:latest`

