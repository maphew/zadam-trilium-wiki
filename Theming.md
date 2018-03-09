Trilium doesn't come (yet) with any built-in themes, but allows you to create custom CSS which is attached to the main HTML page.

Just create a code note with CSS type, put your custom CSS code into the note's content and create "app_css" [[attribute|Attributes]]. When Trilium frontend starts, all notes with "app_css" attribute are appended in the style element of the Trilium HTML page.

Once you made your changes, you can reload the Trilium frontend by pressing CTRL-R after which the changes will take effect.

The reason why the CSS is stored in the (code) note instead of e.g. file in the Trilium folder is that as a note it can be automatically synced and versioned.

## Night mode

```CSS
html, img, video {
    filter: invert(100%) hue-rotate(180deg);
}

body {
    background: black;
}
```

[[images/black-css.png]]

### Grey night mode

Following grey CSS is less contrasty which might be easier on the eyes. The disadvantage is that it casts (barely) noticeable greyish color on the images.

```CSS
html {
    filter: invert(90%) hue-rotate(180deg);
}

img, video {
    filter: invert(100%) hue-rotate(180deg);
}

body {
    background: #191819;
}
```

[[images/grey-css.png]]