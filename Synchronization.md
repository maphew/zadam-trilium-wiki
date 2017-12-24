Trilium supports synchronization with star-shaped topology:

[[images/star-topology.png]]

This means that there's one central server (we'll call this instance _sync server_) and several _client_ instances which all point to this sync server and synchronize against it.

**Beware that synchronization is considered experimental and you should expect occasional issues which might require manual intervention.**

## How to setup synchronization

### Preparation

Here we assume you already have Trilium running on your computer and you want to setup sync server so you can edit same [document](Document.md) online.

Of course you need to install Trilium on the sync server. It's recommended to have exact same version of Trilium installed everywhere. Trilium will reject synchronization if there's a mismatch in Trilium database version between client and sync server.

Before you start the process of setting everything up, it's recommended to stop Trilium on the existing instance.

### Sync server setup

1. Run Trilium in your new environment - this will generate default directory ```trilium-data``` in your home directory, default config etc.
2. Stop Trilium in the new environment
3. Copy your existing trilium [document](Document.md) file (by default located in your home directory under ```trilium-data/document.db```) into your target environment into ```trilium-data``` directory
4. Edit client's ```trilium-data/config.ini``` and set ```syncServerHost``` to the host and port where the sync server is running
5. Start the sync server
6. Start the client

You should be able to see in the client logs that sync connection has been established.

### Additional sync client(s) setup

Setting up extra sync clients is very similar to setting up a server - make sure everything is stopped, copy the [document](Document.md), set up client's ```syncServerHost``` in ```config.ini``` to point to the sync server and then start everything up.

## Conflict resolution

You can sometimes encounter a situation where you edit same note in multiple instances before the note changes are synchronized.

Trilium handles this situation by just picking up the newer change and discarding the older change. The older change should still be visible in history so it should be possible to recover any data lost in conflict resolution.

## Hash check

After each completed sync, Trilium computes hash of all synced data on both client and sync server. If there's a difference, something went wrong and Trilium will notify you about this.