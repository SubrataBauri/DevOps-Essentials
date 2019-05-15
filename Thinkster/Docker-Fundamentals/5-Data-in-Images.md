# Data in Images

## Copying Data

Use COPY command:

`COPY ./html /var/www/html`


## Using Wildcards

`COPY ./html/*.html /var/www/html/`


## The Magic of ADD

`ADD ./html.tar.gz /var/www/` => This will copy the tar file and extract it in the destination

`ADD http://example.com/index.html /var/www/html/example.html` => This will download file from remote url put in the destination

## Ignoring Files

Create `.dockerignore` file to ignore files while COPY
