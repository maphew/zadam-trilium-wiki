Template is a concept related to [[promoted attributes]]. 

Often we have some kind of note "class" - e.g. we want to keep track of books we've read and there are some common attributes we'd like to fill for all such books - we want to have author's name there, link to amazon or wikipedia, genre or publication date.

To make these attributes really obvious, we make them "[[promoted|promoted attributes]]" so they are visible on the UI on the first sight. But we don't want to set them as promoted for each note separately so what we'll do is that we'll create a "Book template" note where we'll define all those promoted attribute.

Then whenever we create a new note for book we'll just link the template to the book note via special system [[relation|Attributes]] `template`. Book note will then automatically inherit all the inheritable attributes from the template note (including the promoted ones) and display them.

To make this even more automated, we can create "child:template" (see [[attribute inheritance]]) attribute on common parent note of our books and whenever we create new note inside this parent, the book note will get the template relation automatically.

You can check out the concept in the [[demo document|Document#demo-document]] in e.g. [[Family tree]], [[Task manager]] or [[Day notes]]. 