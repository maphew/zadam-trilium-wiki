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

Extension is available from the [Project release page](https://github.com/zadam/trilium-web-clipper/releases) - for Firefox (.xpi) and for Chromium based browsers (.zip).

## Install on Chrome

Chromium build will be available on Chrome Web Store, but in the mean time you can follow this guide to install it:

* Download latest chrome build (.zip) of the web clipper from the [release page](https://github.com/zadam/trilium-web-clipper/releases) and unzip it
* Open your Google Chrome web browser.
* Go to chrome://extensions/ and check the box for Developer mode in the top right.
* Click on “Load unpacked” button, and go to the location of this content of the unpacked extension from above. And click on the OK button to install that Chrome extension.

# Configuration

The extension needs to connect to a running Trilium instance. By default it scans a port range on the local computer to find a desktop Trilium instance.

It's also possible to configure [[server|Server installation]] address for cases when the desktop application is not currently running.
