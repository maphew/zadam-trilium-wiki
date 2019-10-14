Note is a central entity in Trilium. Main attributes of note are title and content.

Importantly, note itself doesn't carry information on its placement in note tree.

Tree structure of notes can resemble file system - but compared to that notes in Trilium can act as both file and directory - meaning that note can both have its own content and have children. "Leaf note" is a note which doesn't have any children. 

### Note types

* text note - this is default note type which allows you to put rich text, images etc.
* [[code note|Code notes]] - some kind of formal code, typically programming language (e.g. JavaScript) or data structure (e.g. XML)
* [image note](https://github.com/zadam/trilium/wiki/Images) - represents single image
* file note - represents uploaded file (e.g. docx MS Word document).
* render HTML note - this works as an output screen of attached [[scripts]]
* saved search note - contains saved search query and dynamically displays result of the search as its sub-notes
* [[relation map]] note - visualizes notes and their relations

Remember there's no "folder" note type. Any note can be folder or "leaf" note.

### Root note
There's one special note called "root note" which is root of the note tree. All other notes are placed below it in the structure.