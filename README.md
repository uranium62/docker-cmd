## Docker CMD

```

# version
docker -v
docker version

# info
docker info

# run interactive container
docker run -it ubuntu /bin/bash

# pull docker image
docker pull ubuntu

# remove all stoped containers
docker rm `docker ps --no-trunc -aq`
docker rm -f $(docker ps -q -a)
docker rmi -f $(docker images -q)


# remove image
docker rmi <id>

# remove container 
docker rm <id>



# run service
sudo service docker start

# host 1
docker daemon -H 0.0.0.0:2375

# host 2
docker -H 192.168.0.101:2375 images

#docker copy
docker cp foo.txt mycontainer:/foo.txt
docker cp mycontainer:/foo.txt foo.txt

# Add the docker group if it doesn't already exist.
sudo groupadd docker

# Add the connected user "${USER}" to the docker group.
sudo gpasswd -a ${USER} docker

# Restart the Docker daemon.
sudo service docker restart

# set docker-host
export DOCKER_HOST="tcp://192.168.58.50:2375" 

# restart container
docker run --restart=always redis
`

CTRL+P+Q

# create cluster host1 (push token to doker hub)
swarm create

# join to cluster host1, host2, host3
swarm join token://<token> --addr <ip(host1)>:<port(2375)>
swarm join token://<token> --addr <ip(host2)>:<port(2375)>
swarm join token://<token> --addr <ip(host3)>:<port(2375)>

# show list of host in cluster
swarm list token://<token>

# swarm entrypoint host1
swarm manage token://<token> -H <ip(0.0.0.0)>:<port(4243)> --strategy <(binpacking, randompacking)>
ps -ef | grep swarm
swarm manage --help

# connect to entrypoint
export DOCKER_HOST=<entrypoint:4243>
docker info
docker run --name webserver -p 80:80 -d nginx

# constrains
docker run -d --name webserver1 -e constraint:node==host2 nginx
docker run -d --name webserver2 -e affinity:container==webserver1 nginx

```