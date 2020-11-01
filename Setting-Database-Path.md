# Windows (to be done)
***



# OSx (tested on Catalina)
***

For setting a custom database Path, you have to set it manually.

Specifically for OSx, that has changed, and export isn't enough.
You need to create a file under `~/Library/LaunchAgents` to load it properly each login.

To load it manually, u need to use `launchctl setenv TRILIUM_DATA_DIR <yourpath>`

Here is a pre-defined template, where u just need to add your path to.
https://hastebin.com/egamirumix.xml