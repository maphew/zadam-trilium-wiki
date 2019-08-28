Trilium can be run as docker image. This is recommended way to deploy Trilium on servers.

Docker images are published on docker hub: https://hub.docker.com/r/zadam/trilium/

## Pull image

~~~~
docker pull zadam/trilium:[VERSION]
~~~~

Replace [VERSION] for actual latest version or use "series" tag - e.g. `0.34-latest`.

**It's not recommended to use "latest" tag since it may upgrade your Trilium instance to new minor version which may potentially break your sync setup or cause other issues.**

## Run image

~~~~
sudo docker run -t -i -p 8080:8080 -v ~/trilium-data:/home/[USER]/trilium-data zadam/trilium:latest
~~~~

Command above is mounting volume to the host system so that trilium's data (most importantly [[document]]) is persisted and not cleared after container stops.