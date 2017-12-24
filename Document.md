Document is [SQLite](https://www.sqlite.org) database which contains all notes, metadata, even some of the configuration.

It's stored in single file, by default in ```trilium-data/document.db```

If you want to backup your Trilium data, just backup this single file - it contains everything you need.

Trilium has been originally created as a web interface to the [Notecase Pro](http://www.notecasepro.com/), as such it used same database format as Notecase Pro. Database format evolved and today it's not compatible with Notecase Pro even though there are still some similarities in its schema.