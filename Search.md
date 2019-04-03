Trilium supports searching in notes. There are several ways to search notes:

* full text search - search in text and [[code note|code notes]] content. Since this is implemented as a database search, this works only for not protected notes (doesn't matter if you're in protected session or not)

* [[attribute|Attributes]] search - you can e.g. search for notes having certain label - see *Attribute query syntax* below.

* you can save search string (composed of either fulltext or attribute search) into so-called "saved search" note. If you expand this note, you will see the search results as child notes.
  * saved search can also reference [[scripts|script]] through relation - upon expanding, the script will provide a list of results

You can activate search by clicking on magnifier icon on the left or pressing `CTRL-S` keyboard [[shortcut|keyboard shortcuts]].

## Fulltext

Fulltext search is triggered whenever search string doesn't start with `@` (used in attribute search) or `=` (saved search with script). You can enter any text, but only alpha numeric words are being searched.

Fulltext searches on undeleted, unprotected text and code notes which are not archived.

Fulltext is implemented using Sqlite's [FTS5](https://www.sqlite.org/fts5.html). This provides some advanced functionality, e.g. "NEAR(heavy metal)" will match notes only if a word "heavy" is close to "metal". But since this syntax is quite specific and easy to get it wrong, it is accessible only via `@text` virtual attribute. Such query would then look like this: `@text="NEAR(heavy metal)"`

## Attribute query syntax

Following examples demonstrates syntax:

    <li>Just enter any text for full text search</li>
    <li><code>@abc</code> - returns notes with label abc</li>
    <li><code>@year=2019</code> - matches notes with label <code>year</code> having value <code>2019</code></li>
    <li><code>@rock @pop</code> - matches notes which have both <code>rock</code> and <code>pop</code> labels</li>
    <li><code>@rock or @pop</code> - only one of the labels must be present</li>
    <li><code>@year&lt;=2000</code> - numerical comparison (also &gt;, &gt;=, &lt;).</li>
    <li><code>@dateCreated>=MONTH-1</code> - notes created in the last month</li>
    <li><code>=handler</code> - will execute script defined in <code>handler</code> relation to get results</li>

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

## Auto trigger search from URL

Opening Trilium like in the example below will open search pane and automatically trigger search for "abc":

```
http://localhost:8080/#search=abc
```