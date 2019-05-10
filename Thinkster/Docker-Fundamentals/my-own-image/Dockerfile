## Base image

From debian:buster-slim


## Run the following commands (RUN)

RUN apt-get update
RUN apt-get install -y nginx

### Output log to stdout
RUN rm /var/log/nginx/access.log && ln -s /dev/stdout /var/log/nginx/access.log

## Startup command (CMD)

# CMD nginx -g 'daemon off;'
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]