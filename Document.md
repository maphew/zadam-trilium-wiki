Document is [SQLite](https://www.sqlite.org) database which contains all notes, tree structure, metadata and most of the configuration.

It's stored in single file, by default in `trilium-data/document.db`, where `trilium-data` is stored in:

* `/home/[user]/.local/share` for Linux
* `C:\Users\[user]\AppData\Roaming` for Windows Vista and up
* `/Users/[user]/Library/Application Support` for Mac OS
* user's home if some of the paths above don't exist

If you want to backup your Trilium data, just backup this single file - it contains everything you need.

## Demo document

When you run Trilium for the first time, it will generate a demo document for you as a starting point. It's also pretty useful for demonstration of some of Trilium's features, e.g.:

* [[Relation map]]
* [[Day notes]]
* [[Weight tracker]]
* [[Task manager]]
