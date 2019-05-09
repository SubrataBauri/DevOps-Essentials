## Managing Images through the Docker Client
`docker image ls`

To delete any image, simply run `docker image rm [IMAGE_NAME]:[IMAGE_TAG]`. If no tag is provided, Docker will assume `latest`

To download (or pull) an image from Docker Hub, run `docker image pull [IMAGE_NAME]:[IMAGE_TAG]`

## Docker Login

We can log in to Docker through the Docker Client using your Docker ID `docker login`

## Creating Images
Build your image into a container with: `docker image build -t [image_name]:[tag] [directory]`

Run the newly created image with command: `docker container run -it [image_name]:[tag]`

## Comments
Comments are started with `#` at the beginning of a line

## Pushing Images
While official images live in their own namespace, locally created ones do not. 
We must assign them to our directory with our own Docker ID by calling 
`docker image tag [image_name]:[tag] [docker_ID]/[image_name]:[tag]`

Push image to Docker with: `docker image push [docker_ID]/[image_name]:[tag]`

## Docker Plugins
Ex. `docker plugin install store/weaveworks/net-plugin:2.5.1`

List plugins with `docker plugin ls`

List commands with `docker plugin`

## Using a 3rd Party Registry
Install a third party registry by logging in through your terminal and providing the third party url. 
For example: `docker login quay.io`

You may need to reassign images with a new directory like so:
`docker image tag [old_directory]/[image_name]:[tag] quay.io/[new_directory]/[image_name]:[tag]`

*push* and *pull* using the third party registry:

```
docker image push quay.io/[new_directory]/[image_name]:[tag]  # pushes to quay.io
docker image pull quay.io/[new_directory]/[image_name]:[tag]  # pulls from quay.io
```

# ASSIGNMENT
## Create My Own Image

```
### Base image (FROM)
debian:buster-slim

### Run the following commands (RUN)
apt-get update
apt-get install -y nginx

### Startup command (CMD)
nginx -g 'daemon off;'

### Build the image
* Tag it with <docker_id>/nginx:latest
* Push it to Docker Hub

### Verify the image works
* Start a container
* Expose port 80
* Use a browser

### Stop the container
docker container kill <CONTAINER NAME>
docker container ls
```