Trilium ([[server edition|Server installation]]) has a mobile web frontend which is optimized for touch based devices - smartphones and tablets. It is activated automatically during login process based on browser detection.

Mobile frontend is limited in features compared to full desktop frontend. See below for more details on this.

## Screenshots

### Mobile phone

[[images/mobile-smartphone.png|width=956]]

### Tablet

[[images/mobile-tablet.png|width=420]]

## Limitations

Mobile frontend provides only some of the features of the full desktop frontend:

* it is possible to browse the whole note tree, read and edit all types of notes, but you can create only text notes
* reading and editing [[protected notes]] is possible, but creating them is not supported
* editing options is not supported
* cloning notes is not supported
* uploading file attachments is not supported

## Forcing mobile/desktop frontend

Trilium decides automatically whether to use mobile or desktop frontend. If this is not appropriate, you can use `?mobile` or `?desktop` query param on **login** page (i.e. you might need to log out).