# Deploy Static HTML Website as Container

## Step 1 - Create Dockerfile
The Dockerfile should contain the following content
```
FROM nginx:alpine
COPY . /usr/share/nginx/html
```
Create a index.html file in the same location with any HTML content.

## Step 2 - Build Docker Image
`docker build -t webserver-image:v1 .`

View a list of all the images on the host using `docker images`

## Step 3 - Run
The built Image can be launched in a consistent way to other Docker Images. When a container launches, it's sandboxed from other processes and networks on the host. When starting a container we need to give it permission and access to what it requires.

For example, to open and bind to a network port on the host we need to provide the parameter 

`-p <host-port>:<container-port>`

e.g. `docker run -d -p 80:80 webserver-image:v1`

Once started, we'll be able to access the results of port 80 via `curl docker`

