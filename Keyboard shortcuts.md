This is supposed to be a complete list of keyboard shortcuts. Note that some of these may work only in certain contexts (e.g. in tree pane or note editor).

## Note navigation

* ```CTRL+UP```, ```CTRL+DOWN``` - go up/down in the list of notes
* ```CTRL+LEFT```, ```CTRL+RIGHT``` - collapse/expand node
* ```ALT+LEFT```, ```ALT+RIGHT``` - go back / forwards in the history
* ```CTRL+J``` - show "Jump to" dialog
* ```CTRL+E``` - show "Recent notes" dialog
* ```CTRL+.``` - scroll to current note (useful when you scroll away from your note or your focus is currently in the editor)
* ```ALT+C``` - collapse whole note tree
* ```ALT+-``` (alt with minus sign) - collapse sub-tree (if some subtree takes too much space on tree pane you can collapse it)

See demo of some of these features in [[note navigation|Note navigation]].

## Creating notes

* ```CTRL+O``` - creates new note after the current note
* ```CTRL+P``` - creates new sub-note into current note
* ```F2``` - edit prefix of current note clone

## Moving / cloning notes

* ```SHIFT+UP```, ```SHIFT+DOWN``` - move note up/down in the note list
* ```SHIFT+LEFT``` - move note up in the note tree
* ```SHIFT+RIGHT``` - move note down in the note tree 
* ```CTRL+C``` - copies current note into clipboard (used for [[cloning|Cloning notes]])
* ```CTRL+X``` - cuts current note into clipboard (used for moving notes)
* ```CTRL+V``` - pastes note as sub-note into current note (which is either move or clone depending on whether it was copied or cut into clipboard)
* ```DEL``` / ```CTRL+DEL``` - delete note / sub-tree. Just ```DELETE``` works in tree pane, ```CTRL-DEL``` works globally.

## Editing notes

* ```CTRL+K``` - create / edit external link
* ```CTRL+L``` - create internal (note) link
* ```ALT+T``` - inserts current date and time at caret position

## Runtime shortcuts

These are hooked in Electron to be similar to native browser keyboard shortcuts.

* ```F5```, ```CTRL-R``` - reloads trilium frontend
* ```CTRL+SHIFT+I``` - show developer tools
* ```CTRL+F``` - show search dialog

## Other

* ```CTRL+U``` - show note source (read only)
* ```ALT+O``` - show SQL console (use only if you know what you're doing)
* ```ALT+M``` - distraction-free mode - display only note editor, everything else is hidden
* ```ALT+H``` - show note history
* ```ALT+S``` - toggle search form in tree pane
* ```ALT+R``` - show recent changes dialog
