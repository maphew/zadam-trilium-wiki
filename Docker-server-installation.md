Trilium can be run as docker image. This is recommended way to deploy Trilium on servers.

Docker images are published on docker hub: https://hub.docker.com/r/zadam/trilium/

## Pull image

~~~~
docker pull zadam/trilium:[VERSION]
~~~~

Replace [VERSION] for actual latest version. It's not recommended to use "latest" tag.

## Run image

~~~~
sudo docker run -t -i -p 8080:8080 -v ~/trilium-data:/root/trilium-data zadam/trilium:latest
~~~~

Command above is mounting volume to the host system so that trilium's data (most importantly [[document]]) is persisted and not cleared after container stops.