In general we may say that [[script|scripts]] notes are triggered by events. "run" represents global events:

* `run`
  * `frontendStartup` - executes on frontend upon startup
  * `backendStartup` - executes on backend upon startup
  * `hourly` - executes once an hour on backend 
  * `daily` - executes once a day on backend

Other events are bound to some entity, these are defined as [[relations|Attributes]] - meaning that script is triggered only if note has this script attached to it through relations (or it can inherit it).

* `runOnNoteView` - executes when note is displayed on frontend
* `runOnNoteCreation` - executes when note is created on backend
* `runOnNoteTitleChange` - executes when note title is changed (includes note creation as well)
* `runOnNoteChange`  - executes when note is changed (includes note creation as well)
* `runOnChildNoteCreation`  - executes when new note is created under *this* note
* `runOnAttributeCreation` - executes when new attribute is created under *this* note
* `runOnAttributeChange` - executes when attribute is changed under *this* note