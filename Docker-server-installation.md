Trilium can be run as docker image. This is recommended way to deploy Trilium on servers.

Official docker images are published on docker hub for **AMD64**: https://hub.docker.com/r/zadam/trilium/

Unofficial docker images for **ARMv7** and **ARMv8** provided by Howard (thanks!): https://hub.docker.com/r/hlince/trilium ([build scripts](https://gitea.e9g.rocks/howard/trilium-daily-build))

## Pull image

~~~~
docker pull zadam/trilium:[VERSION]
~~~~

Replace [VERSION] for actual latest version or use "series" tag - e.g. `0.39-latest`.

**It's not recommended to use "latest" tag since it may upgrade your Trilium instance to new minor version which may potentially break your sync setup or cause other issues.**

## Run image

~~~~
sudo docker run -t -i -p 127.0.0.1:8080:8080 -v ~/trilium-data:/root/trilium-data zadam/trilium:[VERSION]
~~~~

Command above is mounting volume to the host system so that trilium's data (most importantly [[document]]) is persisted and not cleared after container stops. 

If you want to run your instance in a non-default way, please use the volume switch as follows: `-v ~/YourOwnDirectory:/root/trilium-data zadam/trilium:[VERSION]`.
It is important to be aware of how Docker works for volumes, with the first path being your own and the second the one to virtually bind to.
https://docs.docker.com/storage/volumes/

X