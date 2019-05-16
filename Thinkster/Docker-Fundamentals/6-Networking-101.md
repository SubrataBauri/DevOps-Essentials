# Networking 101

## Publishing Ports

`docker container run --publish 127.0.0.1:8080:80 -d nginx:latest`


## Publishing Multiple Ports

`docker container run -p 80:80 -p 81:81 -d nginx:latest`

`docker container run -p 80-99:80-99 -d nginx:latest`


## The EXPOSE Instruction

`EXPOSE 80`


## What Will Be Published

`docker container run -p 80 nginx:latest`
`docker container run -P nginx:latest`

**Both will publish ports:** `0.0.0.0:32768->80/tcp`

