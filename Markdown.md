Trilium Notes supports importing Markdown (CommonMark flavor).

## Import

### Clipboard import

If you want to import just a chunk of markdown from clipboard, you can do it from editor block menu:

[[gifs/markdown-inline-import.gif]]

### File import

You can also import Markdown files from files:

* single markdown file (with .md extension)
* whole tree of markdown files (packaged into [.tar](https://en.wikipedia.org/wiki/Tar_(computing)) archive)
  * Markdown files need to be packaged into tar archive because browser can't read directories, only single files.
  * You can use e.g. [7-zip](https://www.7-zip.org) to package directory of markdown files into tar file
  
[[gifs/markdown-file-import.gif]]

## Export

### Subtree export

You can export whole subtree to .tar archive which will have directory structured modelled after subtree structure:

[[gifs/markdown-export-subtree.gif]]

### Single note import

If you want to export just single note without its subtree, you can do it from Note actions menu:

[[gifs/markdown-export-note.gif]]
