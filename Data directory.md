Data directory contains:

* `document.db` - [[document]]
* `config.ini` - instance level settings like port on which the Trilium application runs
* `backup` - contains automatically [[backup]] of documents
* `log` - contains application log files

## Location
Easy way how to find out which data directory Trilium uses is to look at the "About Trilium Notes" dialog (from "Menu" in upper left corner):

[[images/about-trilium-data-dir.png]]

Here's how the location is decided:

Data directory is normally named `trilium-data` and it is stored in:

* `/home/[user]/.local/share` for Linux
* `C:\Users\[user]\AppData\Roaming` for Windows Vista and up
* `/Users/[user]/Library/Application Support` for Mac OS
* user's home is a fallback if some of the paths above don't exist
* user's home is also a default setup for [[docker|Docker server installation]]

If you want to backup your Trilium data, just backup this single file - it contains everything you need.

### Changing the location of data directory

If you want to use some other location for the data directory than the default one, you may change it via TRILIUM_DATA_DIR environment variable to some other location, e.g.:

```
export TRILIUM_DATA_DIR=/home/myuser/data/my-trilium-data
```