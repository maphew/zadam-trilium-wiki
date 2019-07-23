<img align="right" src="https://raw.githubusercontent.com/wiki/zadam/trilium/images/chrome-trilium-web-clipper.png">
Trilium Web Clipper is a web browser extension which allows user to clip text, screenshots, whole pages and short notes and save them directly to Trilium Notes.

Project is hosted [here](https://github.com/zadam/trilium-web-clipper). Firefox and Chrome are supported browsers, but the chrome build should work on other chromium based browsers as well.

Extension works with Trilium Notes 0.34 and newer.

# Functionality

* select text and clip it with context menu (right click)
* click on an image or link and save it through context menu
* save whole page from the popup or context menu
* save screenshot (with crop tool) from either popup or context menu
* create short text note from popup

Trilium will save these clippings as a new note under current [[day note|day notes]]. If there's multiple clippings from the same page (and on the same day), then they will be added to the same note.

# Get it

Extension is available from: 

* [Project release page](https://github.com/zadam/trilium-web-clipper/releases) - .xpi for Firefox and .zip for Chromium based browsers.
* [Chrome Web Store](https://chrome.google.com/webstore/detail/dfhgmnfclbebfobmblelddiejjcijbjm/publish-accepted?authuser=0&hl=en)

# Configuration

The extension needs to connect to a running Trilium instance. By default it scans a port range on the local computer to find a desktop Trilium instance.

It's also possible to configure [[server|Server installation]] address for cases when the desktop application is not currently running.
