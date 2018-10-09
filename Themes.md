Trilium by default comes with few color themes, with white being the default. To switch to dark theme, you just need to go to Options (top-right) -> Appearance tab and change the theme.

This is how it looks like:

[[images/dark-theme.png]]

## Custom CSS

Trilium allows you to create custom CSS which is attached to the main HTML page. With this you can customize the look of Trilium all you want.

This is also useful in the context of [[scripting|scripts]] where you may want to e.g. change colors of notes in the tree (as used in [[Task manager]]).

To do this, just create a [[code note|code notes]] with CSS type, put your custom CSS code into the note's content and create "appCss" [[label|Attributes]]. When Trilium frontend starts, all notes with "appCss" label are appended in the style element of the Trilium HTML page.

Once you made your changes, you can reload the Trilium frontend by pressing CTRL-R after which the changes will take effect.

[[images/app-css.png]]