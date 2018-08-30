This is the easiest and recommended method method on how to install Trilium on your server.

## Steps

* ssh into your server
* use `wget` (or `curl` or whatever) to download latest [
trilium-linux-x64-server-[VERSION].7z](https://github.com/zadam/trilium/releases/latest) (notice -server suffix) on your server
* unpack the archive, e.g. using `p7zip -d`
* `cd trilium-linux-x64-server`
* nohup ./trilium &
  * this will start the trilium application in background and keep it running even after your ssh connection disconnects
* you can open the browser and open http://[your-server-hostname]:8080 and you should see Trilium initialization page

## TLS

Don't forget to [[configure TLS|TLS configuration]], which is required for secure usage!