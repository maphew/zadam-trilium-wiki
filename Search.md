**Text below describes features as of Trilium 0.31**

Trilium supports searching in notes. There are several ways to search notes:

* full text search - search in text and [[code note|code notes]] content. Since this is implemented as a database search, this works only for not protected notes (doesn't matter if you're in protected session or not)

* [[attribute|Attributes]] search - you can e.g. search for notes having certain label - see *Attribute query syntax* below.

* you can save search string (composed of either fulltext or attribute search) into so-called "saved search" note. If you expand this note, you will see the search results as child notes.
  * saved search can also reference [[script|scripts]] through relation - upon expanding, the script will provide a list of results

You can activate search by clicking on magnifier icon on the left or pressing `CTRL-S` keyboard [[shortcut|keyboard shortcuts]].

## Fulltext

Fulltext search is triggered whenever search string doesn't start with `@` (used in attribute search) or `=` (saved search with script). You can enter any text, but only alpha numeric words are being searched.

Fulltext searches on both title and content of undeleted, unprotected text and code notes which are not archived.

Fulltext is implemented using Sqlite's [FTS5](https://www.sqlite.org/fts5.html). This provides some advanced functionality, e.g. "NEAR(heavy metal)" will match notes only if a word "heavy" is close to "metal". But since this syntax is quite specific and easy to get it wrong, it is accessible only via `@text` virtual attribute. Such query would then look like this: `@text="NEAR(heavy metal)"`

## Attribute query syntax

### Standard attributes

Here you query by standard [[attributes]]:

* `@abc` - returns notes with label abc
* `@year=2019` - matches notes with label `year` having value `2019`
* `@year!=2019` - marches notes with label `year`, but not having value 2019 or not having label `year` at all.
  * if you want to express condition that note must have `year` label, but not value 2019, then you can do that with `@year @year!=2019`
* `@year<=2000` - return notes with label `year` having value 2000 or smaller. `>`, `<`, `>=` and `<=` are supported.
  * In this case parameter can be parsed as a number so number-wise comparison is done. But it's also possible to compare strings lexicographically in the same way. This is useful for comparing dates as seen below.
* `@rock @pop` - matches notes which have both `rock` and `pop` labels
  * `@rock and @pop` is an alternative syntax for the same thing
* `@rock or @pop` - only one of the labels must be present
  * `and` has a precedence over `or` in case both operators are used in a search string
* `@frontMan=*John` - matches notes where `frontMan` label starts with "John". There's also `!=*` for "doesn't start with", `*=` for "ends with" and `!*=` for "does not end with", `*=*` for "contains" and `!*=*` for "does not contain"

### Virtual attributes

It's also possible to query by so called "virtual attributes":

* dateCreated - local date of note's creation date in YYYY-MM-DD HH:mm:ss.sss+OOPP where OOPP are hours and minutes of offset compared to UTC (e.g. "+0100" for Central European Time)
* dateModified - local date of last note's modification in YYYY-MM-DD HH:mm:ss.sss+OOPP
* utcDateCreated - UTC date of note's creation date in YYYY-MM-DD HH:mm:ss.sssZ
* utcDateModified - UTC date of last note's modification date in YYYY-MM-DD HH:mm:ss.sssZ
* noteId
* isProtected - 1 if the note is protected, 0 otherwise
* title - useful if you want to search title separately
* content
* type - `text`, `code`, `image`, `file`, `search` or `relation-map`
* mime - e.g. `text/html` for text note
* text - fulltext attribute of both title and content together

### Date comparisons

Attribute values are untyped strings which means that although you can save into it any kind of value like number or date, Trilium doesn't really know what kind of value it is and can't really treat it properly.

Fortunately if we stick to storing dates in YYYY-MM-DD format, we can still do quite a lot since such dates can be correctly compared as strings - e.g. `@dateCreated>=2015-01-01` will return notes which were created since 2015 even though Trilium is doing just string comparison.

What if you want to find notes created in 2015? You can use "starts with" operator (`=*`) like this: `@dateCreated=*2019` - this will match notes with label starting with string "2019" which all notes created in that year will satisfy.

### Smart filters

Trilium supports few special values

* `@dateCreated>=MONTH-1</code> - notes created in the last month</li>

## Saved search

Trilium provides a way to save common search as a note in the note tree. Search results will then appear as subnotes of this "saved search" note. You can see how this works in action:

[[gifs/saved-search.gif]]

## Auto trigger search from URL

Opening Trilium like in the example below will open search pane and automatically trigger search for "abc":

```
http://localhost:8080/#search=abc
```