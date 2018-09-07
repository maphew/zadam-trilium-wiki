Trilium uses awesome [CKEditor 5](https://ckeditor.com/ckeditor-5/) as its editing component.

## Autoformat

CKEditor supports markdown-like editing experience. It recognizes syntax and automatically converts it to rich text. See it in action:

[[gifs/autoformat.gif]]

Complete documentation for this feature is available in [CKEditor documentation](https://ckeditor.com/docs/ckeditor5/latest/features/autoformat.html).

## Cut selection to sub-note

One of the common situations in Trilium is when you're editing a document and it gets somewhat large so you start splitting it up into subnotes - the process is essentially like this:

* select the desired piece of text and cut it into clipboard
* create new subnote & give it name
* paste the content from clipboard into subnote

Trilium provides a way to automate this:

[[gifs/cut-to-subnote.gif]]

You can notice how heading "Formatting" is automatically detected and new subnote is named "Formatting".

This functionality is bound to `CTRL-P` keyboard shortcut. If there's no selection and you press this shortcut, Trilium will create empty subnote. This also works with `CTRL-O` shortcut - the only difference is that new note is created next to the current instead of inside the current.