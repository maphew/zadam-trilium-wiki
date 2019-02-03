Document is [SQLite](https://www.sqlite.org) database which contains all notes, tree structure, metadata and most of the configuration.

## Location
It's stored in single file, by default in `trilium-data/document.db`, where `trilium-data` is stored in:

* `/home/[user]/.local/share` for Linux
* `C:\Users\[user]\AppData\Roaming` for Windows Vista and up
* `/Users/[user]/Library/Application Support` for Mac OS
* user's home is a fallback if some of the paths above don't exist
* user's home is also a default setup for [[docker|Docker server installation]]

If you want to backup your Trilium data, just backup this single file - it contains everything you need.

### Changing the location of the document

If you want to use some other location for the document than the default one, you may change it via TRILIUM_DATA_DIR environment variable to some other location, e.g.:

export TRILIUM_DATA_DIR=/home/myuser/data/my-trilium-data

## Demo document

When you run Trilium for the first time, it will generate a demo document for you as a starting point. It's also pretty useful for demonstration of some of Trilium's features, e.g.:

* [[Relation map]]
* [[Day notes]]
* [[Weight tracker]]
* [[Task manager]]
* [[Custom CSS theme|Themes#custom-css-themes]] *Steel Blue*

### Restoring demo document

In some cases you might want to take a look at the demo document after you deleted it. Or you might want to see if there was something added (sometimes we add a new feature demonstration into demo document). In such case you can just [download .tar archive](https://github.com/zadam/trilium/blob/master/db/demo.tar) of the latest document and import it somewhere into the tree (right click on a note where you want to import the demo document and choose "Import").