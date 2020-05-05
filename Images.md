Trilium supports storing and displaying images. Supported formats are JPEG, PNG and GIF.

Image is actually type of [[note|Tree concepts#note]] placed into the note tree. It's reference can be copied into text note so it is displayed in the text itself.

## Uploading images
To add image to the note, simply drag it from file explorer onto the note editor inside Trilium and image will be uploaded.

[[gifs/upload-image.gif]]

Alternatively you can click on block toolbar and then on "Insert image":

[[images/block-toolbar-insert-image.png]]

You can also copy paste image from web
- Version 0.41.5 and onwards: image will be downloaded and embedded
- Pre version 0.41.5: only the reference is copied and image copy won't be saved in Trilium. Image will not be available if it's deleted or moved from its original location (or you're offline). The workaround is to first save the image to your computer and then add it to Trilium with one of the methods mentioned above.

## Compression

Since Trilium isn't really meant to be primary storage for image data, it attempts to compress and resize (with pretty aggressive settings) uploaded images before storing them to the database. You may then notice some quality degradation. Basic quality settings is available in Options -> Other.

If you want to save images in their original resolution, it is recommended to save them as attachment to note (top-right "Note actions -> Upload file").