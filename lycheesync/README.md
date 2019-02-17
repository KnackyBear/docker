# What is this ?
Based on linuxserver.io project (https://hub.docker.com/r/linuxserver/lychee), this container include the lycheesync plugin.

The lycheesync plugin use my own forked branch from original project by Gustave Pate (https://github.com/GustavePate/lycheesync). It includes some fixes with the new version of lychee front.

# How is it work ?
Until I make some changes to simplify the integration of lycheesync plugin, you have to enter in the container to use lycheesync.

    docker run -it lycheesync /bin/bash

    cd /lycheesync/ && python3 -m lycheesync.sync /sources/ /var/www/localhost/lychee/ /config/lycheesync/conf.json

**Note:** all params depends on your volume in the docker-compose file (or when you start the container)

# Build & Run
To build the image (used in docker-compose file):

    make build

To run the container, use the docker compose file in the lychee directory (https://github.com/jnvinet/docker/blob/master/lychee/lychee-with-sync-compose.yml) :

    docker-compose -f lychee-with-sync-compose.yml up -d

**Note:** this docker-compose file use some environment variables defined in .env (not committed).
An example of this .env could be:

    MARIADB_CONFIG_PATH=<directory to mariadb config files> 
    MYSQL_ROOT_PASSWORD=
    LYCHEE_CONFIG_PATH=<directory to lychee config files>
    LYCHEE_PICTURES_PATH=<directory where lychee store his pictures>
    LYCHEE_SOURCES_PATH=<directory where are stored original photo to sync with lycheesync>
    NFS_IP=<NFS cluster purpose (not mandatory, depends on your own configuration)>
    NFS_PATH_PICTURES=<NFS cluster purpose, directory where are stored originals photos>
    LYCHEE_DBNAME=<database name in mariadb>
    LYCHEE_DBUSER=<username of the lychee db>
    LYCHEE_DBPWD=<password of the lychee db>
    LYCHEE_DBHOST=<hostname where is installed mariadb (with compose file, you can use service name as hostname)>