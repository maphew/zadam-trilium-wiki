## One time sorting

You can sort notes one time by right-clicking parent note in the note tree, Advanced -> Sort notes by ...

## Automatic / permanent sorting

Child notes can be kept sorted by attaching [[labels|Attributes]] to the parent note:

* `#sorted` - enables sorting, can optionally include name of the note's property/label (see details below)
* `#sortDirection` (since Trilium 0.55) - by default ascending, set it to `desc` value to reverse the sort order
* `#sortFoldersFirst` (since Trilium 0.55) - notes with children will be sorted on top

Sorting works by comparing note property or a specific label on the child notes.

There are 3 sorting levels, where the first one has the highest priority and the second (respectively the third) will be applied only if the 2 compared notes are equal based on higher priority comparison.

1. implicit sorting by `#top` label - child notes with this label will appear on the top of the folder.
2. sorting by child's property or a specific label defined on the parent note's `#sorted` label
  a) parent note has `#sorted` with no value - by default sorting will be done alphabetically
  b) parent note has `#sorted=title` or `#sorted=dateModified` or `#sorted=dateCreated` - sorting will be done based on the defined note's property
  c) parent note has `#sorted` label with any other value - this value is the name of the child note's label, whose value will be used for sorting. So e.g. you set `#sorted=myOrder` on the parent note and then child notes will have labels `#myOrder=001`, `#myOrder=002" etc.
3. sorting of "last resort" is alphabetical

All comparisons are made string-wise - e.g. "1" < "2" or "2020-10-10" < "2021-01-15" but also "2" > "10".