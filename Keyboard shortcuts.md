This is supposed to be a complete list of keyboard shortcuts. Note that some of these may work only in certain contexts (e.g. in tree pane or note editor).

## Note navigation

* `UP`, `DOWN` - go up/down in the list of notes, `CTRL-SHIFT-UP` and `CTRL-SHIFT-DOWN` work also from editor
* `LEFT`, `RIGHT` - collapse/expand node
* `ALT+LEFT`, `ALT+RIGHT` - go back / forwards in the history
* `CTRL+J` - show [["Jump to" dialog|Note navigation#jump-to-note]]
* `CTRL+.` - scroll to current note (useful when you scroll away from your note or your focus is currently in the editor)
* `BACKSPACE` - jumps to parent note
* `ALT+C` - collapse whole note tree
* `ALT+-` (alt with minus sign) - collapse sub-tree (if some subtree takes too much space on tree pane you can collapse it)

See demo of some of these features in [[note navigation|Note navigation]].

## Tabs

* `CTRL+click` - (or middle mouse click) on note link opens note in a new tab

Only in desktop (electron build):

* `CTRL+T` - opens empty tab
* `CTRL+W` - closes active tab
* `CTRL+Tab` - activates next tab
* `CTRL+Shift+Tab` - activates previous tab

## Creating notes

* `CTRL+O` - creates new note after the current note
* `CTRL+P` - creates new sub-note into current note
* `F2` - edit [[prefix|Tree concepts#prefix]] of current note clone

## Moving / cloning notes

* `CTRL+UP`, `CTRL+DOWN` - move note up/down in the note list
* `CTRL+LEFT` - move note up in the note tree
* `CTRL+RIGHT` - move note down in the note tree
* `SHIFT+UP`, `SHIFT+DOWN` - multi-select note above/below
* `CTRL+A` - select all notes in the current level
* `SHIFT+click` - multi select note which you clicked on 
* `CTRL+C` - copies current note (or current selection) into clipboard (used for [[cloning|Cloning notes]])
* `CTRL+X` - cuts current (or current selection) note into clipboard (used for moving notes)
* `CTRL+V` - pastes note(s) as sub-note into current note (which is either move or clone depending on whether it was copied or cut into clipboard)
* `DEL` - delete note / sub-tree

## Editing notes

* `ENTER` in tree pane switches from tree pane into note title. Enter from note title switches focus to text editor. `CTRL+.` switches back from editor to tree pane.
* `CTRL+K` - create / edit [[external link|Links]]
* `CTRL+L` - create [[internal (note) link|Links]]
* `ALT+T` - inserts current date and time at caret position
* `CTRL+.` - jump away from the editor to tree pane and scroll to current note

## Runtime shortcuts

These are hooked in Electron to be similar to native browser keyboard shortcuts.

* `F5`, `CTRL-R` - reloads trilium frontend
* `CTRL+SHIFT+I` - show developer tools
* `CTRL+F` - show search dialog

## Other

* `ALT+O` - show SQL console (use only if you know what you're doing)
* `ALT+M` - distraction-free mode - display only note editor, everything else is hidden
* `F11` - toggle full screen
* `CTRL+S` - toggle [[search]] form in tree pane
* `ALT+A` - show note [[attributes]] dialog
