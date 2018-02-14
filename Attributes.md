Note attributes is a set of key-value records owned by (assigned to) given note.

They are used mainly for several things:

* user can use them as tags/labels with optional value - e.g. when catalogizing books, you might add attributes like @year=1999, @genre=sci-fi, @author=Neal Stephenson
* attributes can be used to configure some advanced features / settings - see below
* plugins / scripts can use these to mark notes with some special values / metadata (e.g. note with imported reddit comment will have attribute with comment ID)

Both of these can then be used in filters.

### Show / edit attributes

Click on note -> Note actions -> Attributes (or use keyboard shortcut ```ALT+A```).

### Filter query syntax

Following examples demonstrates syntax:

* ```@abc``` - matches notes with attribute abc
* ```@!abc``` - matches notes without abc attribute (maybe not the best syntax)
* ```@abc=true``` - matches notes with attribute abc having value true
* ```@abc!=true```
* ```@"weird attribute"="weird value"``` - works also with whitespace inside names values
* ```@abc and @def``` - matches notes with both abc and def
* ```@abc @def``` - AND relation is implicit when specifying multiple attributes
* ```@abc or @def``` - OR relation
* ```@abc<=5``` - numerical comparison (also >, >=, <).
* ```some search string @abc @def``` - combination of fulltext and attribute search - both of them need to match (OR not supported)
* ```@abc @def some search string``` - same combination

### Standard attributes

Following attributes are used for advanced configuration:

* ```disable_versioning``` - disables auto-versioning. Useful for e.g. large, but unimportant notes - e.g. large JS libraries used for scripting
* ```calendar_root``` - marks note which should be used as root for "day notes". Only one should be marked as such.
* ```run_on_startup``` - JavaScript notes with this attribute will be executed after Trilium startup
* ```hide_in_autocomplete``` - notes with this attribute won't be visible in autocomplete-based search (jump to, add link). Applies also to all its sub-notes.