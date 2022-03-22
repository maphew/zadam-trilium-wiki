Trilium can be run as docker image. This is recommended way to deploy Trilium on servers.

Official docker images are published on docker hub for **AMD64**, **ARMv6**, **ARMv7** and **ARMv8/64**: https://hub.docker.com/r/zadam/trilium/

## Prerequisites
To start you will need to have docker installed on your computer. Here are two guides that can help:
- https://docs.docker.com/engine/install/ubuntu/
- https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04

## Pull image

~~~~
docker pull zadam/trilium:[VERSION]
~~~~

Replace [VERSION] for actual latest version or use "series" tag - e.g. `0.48-latest`.

**It's not recommended to use "latest" tag since it may upgrade your Trilium instance to new minor version which may potentially break your sync setup or cause other issues.**

## Prepare data directory on the host system

Trilium needs a directory where it can store its data, this then needs to be mounted into the docker container. The container runs as user "node" so we need to make the directory available to this user:

```
mkdir ~/trilium-data
chmod 777 ~/trilium-data
```

Since this effectively allows reading/writing this directory to any user on the system, it's recommended to do this on only single-user systems. This directory will be used (mounted) below.

## Run image
These commands mount the volume to the host system so that trilium's data (most importantly [[document]]) is persisted and not cleared after container stops. 

### Local only
This will run the container so that it only available on the localhost. Use this to test the installation from a web browser on the same machine you run this command on, or if you are using a proxy with nginx/apache. 
~~~~
sudo docker run -t -i -p 127.0.0.1:8080:8080 -v ~/trilium-data:/home/node/trilium-data zadam/trilium:[VERSION]
~~~~
1. Test to see that the docker image is running with `docker ps`
2. Access the trilium by opening a browser and go to `127.0.0.1:8080`

### Local network only
This command will run the container so that it is only available on your local network. This is preferable if you do not want to open ports to the rest of the internet. However, you can still access it from outside by using a VPN like WireGuard to get into your own network first. This method does assume that your local network limits outside access. 

First, you have to create a new network in Docker to access your local network. Here is an example, give note to "parent" and the network numbers as it may differ from your own. For more detailed information, [click here](https://blog.oddbit.com/post/2018-03-12-using-docker-macvlan-networks/).
~~~~
docker network create -d macvlan -o parent=eth0 --subnet 192.168.2.0/24 --gateway 192.168.2.254 --ip-range 192.168.2.252/27 mynet
~~~~

Secondly, you have to adjust the docker run command so it takes this network into account but keep using localhost to limit the accessibility of the ports to the outside world.
~~~~
docker run --net=mynet -d -p 127.0.0.1:8080:8080 -v ~/trilium-data:/home/node/trilium-data zadam/trilium:0.48-latest
~~~~

Finally, use docker inspect to find your local IP address to connect to. You can access this from all your devices connected to the local network as such: [local:ip]:8080.
~~~~
docker ps
docker inspect [container_name] 
~~~~

### Available anywhere
This will run the container as a background process and will be available from any IP address
~~~~
docker run -d -p 0.0.0.0:8080:8080 -v ~/trilium-data:/home/node/trilium-data zadam/trilium:[VERSION]
~~~~
To stop this background docker process use `docker ps` to get the "CONTAINER ID" and then use `docker stop <CONTAINER ID>`

### Different data directory location
If you want to run your instance in a non-default way, please use the volume switch as follows: `-v ~/YourOwnDirectory:/home/node/trilium-data zadam/trilium:[VERSION]`.
It is important to be aware of how Docker works for volumes, with the first path being your own and the second the one to virtually bind to.
https://docs.docker.com/storage/volumes/