Note: forked from https://github.com/dbbaskette/gpdb-docker 

# gpdb-docker
Pivotal Greenplum Database Base Docker Image (4.3.7.1)


## Building the Docker image

You will first need to download the Pivotal Greenplum Database 4.3.7.1 installer (.zip) located at 
https://network.pivotal.io/products/pivotal-gpdb and place it inside the docker working directory.

cd [docker working directory]

docker build -t kevinmtrowbridge/gpdb-docker .


## Running it

    docker run -i -p 5432:5432 -t kevinmtrowbridge/greenplumdb_singlenode

Proof -- login with psql:

    psql -h `docker-machine ip default` -p 5432 -U gpadmin template1


# Container accounts

    root/pivotal
    gpadmin/pivotal


# Using psql in the container

    su - gpadmin
    psql


# Using pgadmin or psql outside the container

gpadmin password is: secret

* Launch pgAdmin3 -- create new connection using IP Address and Port # (5432)

- or -
    
    psql -h <docker-machine ip / localhost> -p 5432 -U gpadmin template1


## Other useful Docker commands:

    docker build -t kevinmtrowbridge/greenplumdb_singlenode .
    docker run -i -p 5432:5432 -t greenplumdb_singlenode
    docker ps ... docker exec -it <running container name> bash

### Viewing the logs:

    docker exec -it <running container name> bash
    tail -f /gpdata/master/gpseg-1/pg_log/*


## Docker hub

On Docker Hub here: https://hub.docker.com/r/kevinmtrowbridge/gpdb-docker
