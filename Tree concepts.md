This page describes some basic concepts related to the tree structure of notes in Trilium.

## Note

Note is a central entity in Trilium. Main attributes of note are title and content.

Importantly, note itself doesn't carry information on its placement in note tree.

Tree structure of notes can resemble file system - but compared to that notes in Trilium can act as both file and directory - meaning that note can both have its own content and have children. "Leaf note" is a note which doesn't have any children. 

### Root note
There's one special note called "root note" which is root of the note tree. All other notes are placed below it in the structure.

## Branch

Branch describes note placement in the note tree - in essence it's a tuple of parentNoteId and noteId which says that given note is placed as a child into this parent note.

Each note can have more than one such branches, in other words any note can have multiple placements in the tree. For lack of better word we call this "[[cloning|Cloning notes]]".

## Prefix

Prefix is branch (placement) specific title prefix for the note. Let's say you have your note placed into two different places in the tree, but you want to change the title a bit in one of the placements. For this you can use prefix.

To edit prefix, right click on a note in the tree pane and choose "Edit branch prefix".

## Subtree

Subtree is a set of notes consisting of a particular note (subtree root) and all its children, children of these children (= all its descendants). Some operations work on subtrees (e.g. export).