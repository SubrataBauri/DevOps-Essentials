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


## Links (Deprecated)

`docker container run --name webserver --rm -d nginx:latest`
`docker container run --link webserver -it alpine:latest`


## User Defined Networks

```
docker network ls
docker network create [NAME-OF-NETWORK-HERE]
docker network inspect [NAME-OF-NETWORK-HERE]

docker container run --rm -it --name [NAME-OF-CONTAINER-HERE] --network [NAME-OF-NETWORK-HERE] alpine sh
```

Check with: `ip addr` inside shell of container


## Resolving Hostnames

`docker container run --network mynet --rm -it --name c1 alpine:latest sh`
`docker container run --network mynet --rm -it --name c2 alpine:latest sh`

Stop c2 and start again with different IP, it will still be reached from c1.

`docker container run --network mynet --rm -it --ip 172.19.0.99 --name c2 alpine:latest sh`

## User Defined Networks and Links

**With alias:** `docker container run --network mynet --link webserver:wb -it --rm alpine:latest`

## Sharing Names
`docker container run --network mynet -d --network-alias webserver alpine:latest` => **Create multiple**

Create another container:

`docker container run --network mynet -it alpine:latest`
`nslookup webserver`

All the servers will have same name with different IP