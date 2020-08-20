This is essentially Trilium sources + node modules + node.js runtime packaged into one 7z file.

## Steps

* ssh into your server
* use `wget` (or `curl` or whatever) to download latest [
trilium-linux-x64-server-[VERSION].7z](https://github.com/zadam/trilium/releases/latest) (notice -server suffix) on your server
* unpack the archive, e.g. using `p7zip -d trilium-linux-x64-server-[VERSION].7z`
* `cd trilium-linux-x64-server`
* `./trilium.sh`
* you can open the browser and open http://[your-server-hostname]:8080 and you should see Trilium initialization page

The problem with above steps is that once you close the SSH connection, trilium process is terminated. To avoid that, kill it (with e.g. `CTRL-C`) and run again like this: `nohup ./trilium &`

## Common issues

### Outdated glibc

```
Error: /usr/lib64/libstdc++.so.6: version `GLIBCXX_3.4.21' not found (required by /var/www/virtual/.../node_modules/@mlink/scrypt/build/Release/scrypt.node)
    at Object.Module._extensions..node (module.js:681:18)
    at Module.load (module.js:565:32)
    at tryModuleLoad (module.js:505:12)
```

If you get an error like this, you need to either upgrade your glibc (typically by upgrading to up to date distribution version) or use some other [[server installation]] method.

## TLS

Don't forget to [[configure TLS|TLS configuration]], which is required for secure usage!
