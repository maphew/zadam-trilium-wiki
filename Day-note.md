A common pattern in note taking is that a lot of notes will be centered around certain date - e.g. you have some tasks which needs to be done on certain date, you have meeting minutes from certain date, you have your thoughts etc. and it all revolves around a date on which they occurred. For this reason it makes sense to create certain "day workspace" which will centralize all those notes relevant for certain date.

For this, Trilium provides a concept of "day note". Trilium semi-automatically generates a single note for each day. Under this note you can save ([[clone|Cloning notes]]) all those relevant notes.

## Demo
[[gifs/day-note.gif]]

In the demo you can see clicking on "Today" button (actually a [[script|Scripts]]) which will show today's "day note". Day note itself is empty except for showing list of edited notes that day (this functionality is also provided by script), but contains today's important and relevant notes.

This pattern works well also because of [[cloning|Cloning notes]] functionality - note can appear in multiple places in the note tree so besides appearing under day note, it can also be categorized into other notes (e.g. "Trusted timestamping" note is also categorized under Tech -> Security note).

## Automation

In the demo you can notice that day note has a label - `@dateNote=2018-08-16`. This is useful for scripts to understand the date hierarchy. As an example, you can have a script which will download your reddit comments and save them automatically under day note (on which the comments have been created).