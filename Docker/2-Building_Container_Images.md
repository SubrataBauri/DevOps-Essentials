# Building Container Images

## Step 1 - Base Images
All Docker images start from a base image. A base image is the same images from the Docker Registry which are used to start containers. Along with the image name, we can also include the image tag to indicate which particular version we want, by default, this is latest.

e.g. `FROM nginx:1.11-alpine`

## Step 2 - Running Commands
`RUN <command>` allows you to execute any command as you would at a command prompt, for example installing different application packages or running a build command.

`COPY <src> <dest>` allows you to copy files from the directory containing the Dockerfile to the container's image

e.g. `COPY index.html /usr/share/nginx/html/index.html`

## Step 3 - Exposing Ports
Using the `EXPOSE <port>` command we tell Docker which ports should be open and can be bound too. We can define multiple ports on the single command, 

e.g. `EXPOSE 80 433` or `EXPOSE 7000-8000`

## Step 4 - Default Commands
#### Protip
```
An alternative approach to CMD is ENTRYPOINT. 
While a CMD can be overridden when the container starts, 
a ENTRYPOINT defines a command which can have arguments passed to it when the container launches.
```
e.g. `CMD ["nginx", "-g", "daemon off;"]`
e.g. `ENTRYPOINT ["nginx", "-g", "daemon off;"]`

## Step 5 - Building Containers
After writing your Dockerfile we need to use `docker build` to turn it into an image.

#### Protip
We can use `docker images` to see a list of the images on your local machine.

## Step 6 - Launching New Image
`docker run -d -p 80:80 <image-id|friendly-tag-name>`

e.g. `docker run -d -p 80:80 my-nginx-image:latest`

#### Protip
We can check the container is running using `docker ps`
