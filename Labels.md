Note labels is a set of key-value records owned by (assigned to) given note.

They are used mainly for several things:

* user can use them as tags/labels with optional value - e.g. when catalogizing books, you might add labels like @year=1999, @genre=sci-fi, @author=Neal Stephenson
* labels can be used to configure some advanced features / settings - see below
* plugins / scripts can use these to mark notes with some special values / metadata (e.g. note with imported reddit comment will have label with comment ID)

Both of these can then be used in filters.

### Show / edit labels

Click on note -> Note actions -> Labels (or use keyboard shortcut ```ALT+A```).

### Filter query syntax

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

### Standard labels

Following labels are used for advanced configuration:

* ```disable_versioning``` - disables auto-versioning. Useful for e.g. large, but unimportant notes - e.g. large JS libraries used for scripting
* ```calendar_root``` - marks note which should be used as root for "day notes". Only one should be marked as such.
* ```run_on_startup``` - JavaScript notes with this label will be executed after Trilium startup
* ```hide_in_autocomplete``` - notes with this label won't be visible in autocomplete-based search (jump to, add link). Applies also to all its sub-notes.
* ```exclude_from_export``` - notes (with their sub-tree) won't be included in any note export
* ```run``` - defines on which events script should run. Possible values are:
  * ```frontend_startup``` - when Trilium frontend starts up (or is refreshed).
  * ```backend_startup``` - when Trilium backend starts up
  * ```hourly``` - run once an hour
  * ```daily``` - run once a day
* ```disable_inclusion``` - scripts with this label won't be included into parent script execution.