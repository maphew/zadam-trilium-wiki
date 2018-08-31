Trilium supports searching in notes. In essence it consists of

* [[attribute|Attributes]] search - you can e.g. search for notes having certain label - see *Attribute query syntax* below.
* full text search - search in text and code note content. Since this is implemented as a database search, this works only for not protected notes (doesn't matter if you're in protected session or not)

You can activate search by clicking on magnifier icon on the left or pressing `CTRL-S` keyboard shortcut.

## Attribute query syntax

Following examples demonstrates syntax:

* ```@abc``` - matches notes with label abc
* ```@!abc``` - matches notes without abc label (maybe not the best syntax)
* ```@abc=true``` - matches notes with label abc having value true
* ```@abc!=true```
* ```@"weird label"="weird value"``` - works also with whitespace inside names values
* ```@abc and @def``` - matches notes with both abc and def
* ```@abc @def``` - AND relation is implicit when specifying multiple labels
* ```@abc or @def``` - OR relation
* ```@abc<=5``` - numerical comparison (also >, >=, <).
* ```some search string @abc @def``` - combination of fulltext and label search - both of them need to match (OR not supported)
* ```@abc @def some search string``` - same combination


## Saved search

Trilium provides a way to save common search as a note in the note tree. Search results will then appear as subnotes of this "saved search" note. You can see how this works in action:

[[gifs/saved-search.gif]]