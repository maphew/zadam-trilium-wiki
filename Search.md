Trilium supports searching in notes. There are several ways to search notes:

* local search - searches within currently displayed note. Press `CTRL-F` to open the search dialog. In server version this is handled by the browser, in desktop (electron) version there's a separate dialog.

* note search - you can find notes by search for text in the title, note's content or note's [attributes]. You can also [[save search|saved search]].
  * You can activate note search by clicking on magnifier icon on the left or pressing `CTRL-S` keyboard [[shortcut|keyboard shortcuts]].

## Simple note search examples

`rings tolkien` - will try to find notes which have anywhere words "rings" and "tolkien"

`"The Lord of the Rings" Tolkien` - same as above but "The Lord of the Rings" must be exact match

`towers #book` - searches notes containing "towers" word anywhere and they also need to have "book" label

`towers #book or #author` - searches notes containing "towers" word anywhere and matching note must have either "book" or "author" label

`towers #!book` - searches notes containing "towers" word anywhere and which do **not** have "book"

`#book #publicationYear = 1954` - will find notes with "book" label and label "publicationYear" containing this specific value

`#genre *=* fan` - matches notes with "genre" label which has value which contains "fan" substring. Besides `*=*` for "contains", there's also `=*` for "starts with", `*=` for "ends with", `!=` for "is not equal to" 

`#book #publicationYear >= 1950 #publicationYear < 1960` - you can also use numeric operators - this will find all books published in 1950s

`#dateNote >= TODAY-30` - special "smart search" will find notes with label "dateNote" with date corresponding to last 30 days. Complete list of smart values: NOW +- seconds, TODAY +- days, WEEK +- weeks, MONTH +- months, YEAR +- years

`~author.title *=* Tolkien` - find notes which have relation "author" which points to a note with title containing word "Tolkien"

## Advanced use cases

`~author.relations.son.title = 'Christopher Tolkien'` - This will search for notes which have “author” relation to a note which has a “son” relation to “Christopher Tolkien” note. This situation can be modeled by this note structure:

* Books
  * Lord of the Rings
     * label: “book”
     * relation: “author” points to “J. R. R. Tolkien” note
* People
  * J. R. R. Tolkien
    * relation “son” points to "Christopher Tolkien" note
  * Christoper Tolkien

`~author.title *= Tolkien OR (#publicationDate >= 1954 AND #publicationDate <= 1960)` - you can also use boolean expressions and parenthesis to group expressions

`note.parents.title = 'Books'` will find all notes who have parent note with name “Book”.

`note.parents.parents.title = 'Books'` This again works transitively so this will find notes whose parent of parent is named ‘Book’.

`note.ancestors.title = 'Books'` This is sort of extension of parents - this will find notes which have an ancestor anywhere in their note path (so parent, grand-parent, grand-grand-parent …) with title ‘Book’. This is a nice way how to reduce scope of the search to a particular sub-tree.
                                 
`note.children.title = 'sub-note'` So this works in the other direction and will find notes which have a child called “sub-note”.
          
### Search with note properties

Note has certain properties which can be also used for searching:

* dateModified
* dateCreated
* utcDateModified
* utcDateCreated
* isProtected
* type (text, code, search, relation-map, book)
* title (when you want to search specifically the title)
* text - search through note title, 
* labelCount
* relationCount
* attributeCount - labelCount + relationCount
* parentCount
* childrenCount
* isArchived

These are accessed through `note.`, e.g.:

```
note.type = code
```
          
### Order by and limit

```
#author=Tolkien orderBy #publicationDate desc, note.title limit 10
```

Example above will do the following things (in this sequence):

1.  find notes with label author having value “Tolkien”
2.  order the results by publicationDate in descending order (so newest first)
    1.  in case publication date is equal, use note.title as secondary ordering in ascending order
3.  take only the first 10 results  


## Fulltext

Fulltext search is triggered whenever search string doesn't start with `#` (used in attribute search). 

Fulltext searches on both title and content of undeleted, unprotected text and code notes which are not [[archived|archived notes]].

Input string is tokenized by whitespace separators and each individual token (word) must be present in the title, content or note's attributes. If you don't want this automatic tokenization, you can surround your search with double quotes, e.g. `"hello world"` will search for exact match.

## Attribute query syntax

### Standard attributes

Here you query by standard [[attributes]]:

* `#abc` - returns notes with label abc. `~abc` will look for notes with relation abc.
* `#!abc` - returns notes which don't have label abc
* `#year = 2019` - matches notes with label `year` having value `2019`
* `#year != 2019` - matches notes with label `year`, but not having value 2019 or not having label `year` at all.
  * if you want to express condition that note must have `year` label, but not value 2019, then you can do that with `#year #year != 2019`
* `#year <= 2000` - return notes with label `year` having value 2000 or smaller. `>`, `<`, `>=` and `<=` are supported.
  * In this case parameter can be parsed as a number so number-wise comparison is done. But it's also possible to compare strings lexicographically in the same way. This is useful for comparing dates as seen below.
* `#rock #pop` - matches notes which have both `rock` and `pop` labels
  * `#rock and #pop` is an alternative syntax for the same thing
* `#rock or #pop` - only one of the labels must be present
  * `and` has a precedence over `or` in case both operators are used in a search string
* `#frontMan =* John` - matches notes where `frontMan` label starts with "John". There's also `*=` for "ends with" and `*=*` for "contains".

### Virtual attributes

It's also possible to query by so called "virtual attributes":

* `dateCreated` - local date of note's creation date in YYYY-MM-DD HH:mm:ss.sss+OOPP where OOPP are hours and minutes of offset compared to UTC (e.g. "+0100" for Central European Time)
* `dateModified` - local date of last note's modification in YYYY-MM-DD HH:mm:ss.sss+OOPP
* `utcDateCreated` - UTC date of note's creation date in YYYY-MM-DD HH:mm:ss.sssZ
* `utcDateModified` - UTC date of last note's modification date in YYYY-MM-DD HH:mm:ss.sssZ
* `noteId`
* `isProtected` - 1 if the note is protected, 0 otherwise
* `title` - useful if you want to search title separately
* `content`
* `type` - `text`, `code`, `image`, `file`, `book`, `search` or `relation-map`
* `mime` - e.g. `text/html` for text note
* `text` - fulltext attribute of both title and content together
  * For example `@text*=*Hello`. So that you can combine searching for both text and attributes.
* `isArchived` - filters only for [[archived notes]], `@!archived` then filters only for non-archived notes. Note that this filter does not work in OR relation, it is always AND.
* `in` - for example `@in=VuvLpfAPx2L9` will filter only notes which have note with noteId `VuvLpfAPx2L9` as one of the ancestors - i.e. note is in the subtree of `VuvLpfAPx2L9`. With negating operator - `@in!=VuvLpfAPx2L9` will filter notes which don't have note `VuvLpfAPx2L9` as their ancestor. Since Trilium 0.37

### Order and limit

It's possible to order the results by one or more attribute, e.g. `@orderBy=year,-genre` will order notes by `year` label in ascending order and then by `genre` label in descending order (because of `-` sign).

You can also limit the number of results using e.g. `@limit=1` will return only the first result. If there's no `limit`, then all notes are returned.

### Date comparisons

Attribute values are untyped strings which means that although you can save into it any kind of value like number or date, Trilium doesn't really know what kind of value it is and can't really treat it properly.

Fortunately if we stick to storing dates in YYYY-MM-DD format, we can still do quite a lot since such dates can be correctly compared as strings - e.g. `@dateCreated>=2015-01-01` will return notes which were created since 2015 even though Trilium is doing just string comparison.

What if you want to find notes created in 2015? You can use "starts with" operator (`=*`) like this: `@dateCreated=*2019` - this will match notes with label starting with string "2019" which all notes created in that year will satisfy.

### Smart filters

Trilium supports few special values which will might help you with some search queries:

* `NOW` means this instant to second precision, e.g. `2019-04-01 10:12:54`
  * `NOW-3600` means 1 hour ago
* `TODAY` means today with the day precision, e.g. `2019-04-01`
  * `TODAY-1` means yesterday, `TODAY+1` means tomorrow
* `MONTH` means this month, e.g. `2019-04`
  * `MONTH-1` means last month - i.e. `2019-03`
* `YEAR` means current year, e.g. `2019`
  * `YEAR-1` means last year - 2018

Using this you can create queries like:

* `@dateModified>=NOW-3600` - show me notes changed in the last hour
* `@dateCreated=*TODAY-1` - show me notes created during whole yesterday


## Auto trigger search from URL

Opening Trilium like in the example below will open search pane and automatically trigger search for "abc":

```
http://localhost:8080/#search=abc
```
