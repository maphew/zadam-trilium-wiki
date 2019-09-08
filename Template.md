Template is a note which serves as a kind of "template" for other kind of notes (let's call them instance notes). There are two properties:

* all attributes from the template note are [[inherited|attribute inheritance]] to the instance notes
* note content is copied from the template note to the instance note (if the instance note content is empty at the time of template attribute assignment)

A typical example would be a "Book" template note which will define some [[promoted attributes]] - e.g. publication year, author etc, you can also create kind of outline of the book review in the note text - e.g. themes, conclusion etc. .. And then we have instance note - this note has a [[relation|attributes]] to the "Book" template note which will cause that the template note text is used to initialize the instance note text and all attributes from the template note are inherited to the instance note.

You can check out the concept in the [[demo document|Document#demo-document]] in e.g. [[Relation map]], [[Task manager]] or [[Day notes]]. 
