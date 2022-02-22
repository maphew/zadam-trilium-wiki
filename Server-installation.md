This pages describes installing Trilium on your own server. You might want to do this in case you want to set up [[sync|Synchronization]] or you want to use it as online version of Trilium accessible from anywhere.

There are several options how to do this, each one with some advantage:

* Recommended: [[Docker|Docker server installation]] - images for **AMD64** and **ARM**
* [[Packaged server installation]]
* There's a [3rd party paid service to host a Trilium instance for you](https://trilium.cc/paid-hosting)
* [[Manual installation|Manual server installation]]
* [[Kubernetes|Kubernetes server installation]]
* [Cloudron](https://www.cloudron.io/store/com.github.trilium.cloudronapp.html)
* [HomelabOS](https://homelabos.com/docs/software/trilium/)

Server installation has both web and [[mobile frontend]].

## Configuration

For server installations, you might want to configure e.g. port or [[TLS|TLS configuration]]. This is done in the Trilium config file, by default it's in `config.ini` in the [[data directory]].

### Config location

`config.ini`, [[document]] and some other important Trilium data files are by default persisted in the [[data directory]].

If this is not desired, you may change it via `TRILIUM_DATA_DIR` environment variable to some other location, e.g.:

```bash
export TRILIUM_DATA_DIR=/home/myuser/data/my-trilium-data
```

### Disable authentication
Among others, you can also disable authentication (in case you run on localhost only or authentication is handled by another component) by adding the following to `config.ini`:

```
[General]
noAuthentication=true
```

## Reverse proxy setup

### nginx

```
location /trilium/ {
    proxy_pass http://127.0.0.1:8080/;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
}
```

It's also advised to add following to `server {}` block to not limit size of payloads:

```
# set to 0 for unlimited. Default is 1M.
client_max_body_size 0;
```

### Apache

See [[Apache proxy setup]].