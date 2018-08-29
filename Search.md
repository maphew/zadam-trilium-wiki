

## Filter query syntax

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
