This pages describes installing Trilium on your own server. You might want to do this in case you want to setup [[sync|Synchronization]] or you want to use it as online version of Trilium accessible from anywhere.

There are three options how to do this, each one with some advantage:

* Recommended: [[Docker|Docker server installation]]
* [[Packaged server installation]]
* [[Manual installation|Manual server installation]]

Server installation has both desktop and [[mobile frontend]].

## Configuration

For server installations, you might want to configure e.g. port or [[TLS|TLS configuration]]. This is done in the Trilium config file, by default it's in ~/trilium-data/config.ini (where ~ is your home directory).

### Config location

`config.ini`, [[document]] and some other important Trilium data files are by default persisted in `trilium-data` directory placed in your home directory.

If this is not desired, you may change it via `TRILIUM_DATA_DIR` environment variable to some other location, e.g.:

```bash
export TRILIUM_DATA_DIR=/home/myuser/data/my-trilium-data
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