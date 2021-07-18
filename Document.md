Document is [SQLite](https://www.sqlite.org) database which contains all notes, tree structure, metadata and most of the configuration.

## Location

Document is stored in the [[data directory]].

## Demo document

When you run Trilium for the first time, it will generate a demo document for you as a starting point. It's also pretty useful for demonstration of some of Trilium's features, e.g.:

* [[Relation map]]
* [[Day notes]]
* [[Weight tracker]]
* [[Task manager]]
* [[Custom CSS theme|Themes#custom-css-themes]] *Steel Blue*

### Restoring demo document

In some cases you might want to take a look at the demo document after you deleted it. Or you might want to see if there was something added (sometimes we add a new feature demonstration into demo document). In such case you can just [download .zip archive](https://github.com/zadam/trilium/raw/stable/db/demo.zip) of the latest document and import it somewhere into the tree (right click on a note where you want to import the demo document and choose "Import").

## Manually modifying the document

Trilium provides a lot of flexibility, but with that you can also potentially shoot yourself in the foot (e.g. with startup script which blanks the app view).

In such cases you can manually fix notes on the database layer - you can use e.g. [https://sqlitebrowser.org/](https://sqlitebrowser.org/) to open `document.db` file, find problematic notes and manually fix them. Don't forget to commit / write changes after you're done.