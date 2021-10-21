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

Replace [VERSION] for actual latest version or use "series" tag - e.g. `0.39-latest`.

**It's not recommended to use "latest" tag since it may upgrade your Trilium instance to new minor version which may potentially break your sync setup or cause other issues.**

## Run image
These commands mount the volume to the host system so that trilium's data (most importantly [[document]]) is persisted and not cleared after container stops. 

### Local only
This will run the container so that it only available on the localhost. Use this to test the installation from a web browser on the same machine you run this command on, or if you are using a proxy with nginx/apache. 
~~~~
sudo docker run -t -i -p 127.0.0.1:8080:8080 -v ~/trilium-data:/home/node/trilium-data zadam/trilium:[VERSION]
~~~~
1. Test to see that the docker image is running with `docker ps`
2. Access the trilium by opening a browser and go to `127.0.0.1:8080`

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
