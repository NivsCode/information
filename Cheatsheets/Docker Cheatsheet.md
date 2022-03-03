# Cheatsheet

```terminal
# To check the version
docker version

# Logging in to the cli
docker login -u <username>

# To build a container (-t tag )
# This should be run from the dir where the dockerfile is present
docker build -t <project_tag> .

# To run a container
# (v - flag to specify a volume mount /bind mount; 
# d - detached mode;
# p - port)
docker run -dp 3000:3000 -v <db_filepath> <project_name>

# To check the pos=rts hats that is hosting the app
docker port [CONTAINER]

# To list all running containers
docker ps

# to stop an remove exited containers in one cmd
docker rm $(docker ps -a -q -f status=exited)
# or
docker container prune

# To stop the container with the id
docker stop <id>

# To remove the container
docker rm <the-container-id>

# Tagging a image
docker tag <tagname> tidierink/getting-started

# Pushing the image to docker hub
docker push tidierink/getting-started:<tagname>

# Running commands within the docker
docker exec <container-id> cat /data.txt

# creating a volume
docker volume create todo-db

# Filepath to the db stage cmd (MountPoint)
docker volume inspect

# Logs
docker logs -f <container-id>

# Create a network
docker network create <network_name>

# To create a mysql container within a network
docker run -d \
     --network todo-app --network-alias mysql \
     -v todo-mysql-data:/var/lib/mysql \
     -e MYSQL_ROOT_PASSWORD=secret \
     -e MYSQL_DATABASE=todos \
	 --platform linux/x86_64 \
     mysql:5.7

# To confirm we have the database up and running, connect to the database and verify it connects.

docker exec -it <mysql-container-id> mysql -u root -p

# To run services with docker compose
docker-compose up -d

# BEST PRACTICES
# scanning the image for security issues
docker scan <image-name>

# Getting image history / background on each layer
docker image history op<--no-trunc> <project_name>

```


# Tags
#cheatsheet 