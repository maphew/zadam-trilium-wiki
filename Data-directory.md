Data directory contains:

* `document.db` - [[document]]
* `config.ini` - instance level settings like port on which the Trilium application runs
* `backup` - contains automatically [[backup]] of documents
* `log` - contains application log files

## Location
Easy way how to find out which data directory Trilium uses is to look at the "About Trilium Notes" dialog (from "Menu" in upper left corner):

[[images/about-trilium-data-dir.png]]

Here's how the location is decided:

Data directory is normally named `trilium-data` and it is stored in:

* `/home/[user]/.local/share` for Linux
* `C:\Users\[user]\AppData\Roaming` for Windows Vista and up
* `/Users/[user]/Library/Application Support` for Mac OS
* user's home is a fallback if some of the paths above don't exist
* user's home is also a default setup for [[docker|Docker server installation]]

If you want to backup your Trilium data, just backup this single file - it contains everything you need.

### Changing the location of data directory

If you want to use some other location for the data directory than the default one, you may change it via TRILIUM_DATA_DIR environment variable to some other location:

#### Linux

```
export TRILIUM_DATA_DIR=/home/myuser/data/my-trilium-data
```

#### Mac OS X

You need to create a .plist file under `~/Library/LaunchAgents` to load it properly each login.

To load it manually, u need to use `launchctl setenv TRILIUM_DATA_DIR <yourpath>`

Here is a pre-defined template, where you just need to add your path to:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">
    <dict>
        <key>Label</key>
        <string>set.trilium.env</string>
        <key>RunAtLoad</key>
        <true/>
        <key>ProgramArguments</key>
        <array>
            <string>launchctl</string>
            <string>setenv</string>
            <string>TRILIUM_DATA_DIR</string>
            <string>/Users/**YourUserName**/Library/Application Support/trilium-data</string>
        </array>
    </dict>
</plist>
```

### Create a script to run with specific data directory

And alternative to globally setting environment variable is to run only the Trilium Notes with this environment variable. This then allows for different setup styles like two [[document]] instances or "portable" installation.

To do this in unix based systems simply run trilium like this:

```
TRILIUM_DATA_DIR=/home/myuser/data/my-trilium-data trilium
```

You can then save the above command as a shell script on your path for convenience.