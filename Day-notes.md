A common pattern in note taking is that a lot of notes will be centered around certain date - e.g. you have some tasks which needs to be done on certain date, you have meeting minutes from certain date, you have your thoughts etc. and it all revolves around a date on which they occurred. For this reason it makes sense to create certain "day workspace" which will centralize all those notes relevant for certain date.

For this, Trilium provides a concept of "day note". Trilium semi-automatically generates a single note for each day. Under this note you can save all those relevant notes.

This pattern works well also because of [[cloning|Cloning notes]] functionality - note can appear in multiple places in the note tree so besides appearing under day note, it can also be categorized into other notes.

## Demo
[[images/day-notes.png]]

You can see structure of day notes appearing under "Journal" note - there's a note for the whole year 2017, under it you have "12 - December" which then contains "18 - Monday". This is our "day note" which contains some text in its content and also has some child notes (some of them are from [[Task manager]]).

You can also notice how this day note has [[promoted attribute|Promoted attributes]] "weight" where you can track your daily weight. This data is then used in [[Weight tracker]].

## Implementation

Trilium has some special support for day notes in the form of [backend Script API](https://zadam.github.io/trilium/backend_api/BackendScriptApi.html) - see e.g. getDateNote() function.

Day (and year, month) notes are created with a label - e.g. `@dateNote=2018-08-16` this can then be used by other scripts to add new notes to day note etc.

Journal also has relation "child:child:child:template=Day template" (see [[attribute inheritance]]) which effectively adds [[template]] to day notes (grand-grand-grand children of Journal).
