**As of v0.46 this page is outdated**

Trilium provides a way to save common search as a note in the note tree. Search results will then appear as subnotes of this "saved search" note. You can see how this works in action:

### Saved search with script relation

If saved search string starts with `=`, then the following string is taken as a relation name and the target script is executed to get the list of note results.

So let's say the search string is `=handler`, then Trilium tries to find this saved note's relation with name "handler". Relation is expected to point to [[script|scripts]] which is then executed - script is expected to return a list of notes which should be presented as search results. This option exists for use cases where normal attribute/fulltext search doesn't cover all needs.