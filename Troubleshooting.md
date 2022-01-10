Trilium is currently beta quality software, so it's quite expected there will be some bugs.

## General quickfix

You guessed it - it's restart.

If there's a UI problem, it usually means that the Trilium frontend got into an inconsistent state and is acting up. The easiest way to fix it is to reload the application - just press `CTRL-R` and frontend will be reloaded.

If this still doesn't help, or you suspect it's actually a backend issue, you can restart the whole application - in case of desktop (Electron) build, you just close the window and re-open it again.

## Forgotten username/password

In case you forgot your password, this means that:

* your protected notes are forever lost - they cannot be decrypted without the password
* normal (unprotected) notes are recoverable. Read below to see how.

To be able to change username/password and thus recover your unprotected notes, you need to get access to the [[document]] file in a [[data directory]]. You then need to open the `document.db` file with SQLite client (command line or e.g. [DB Browser](https://sqlitebrowser.org/)) and execute following queries:

```sql
UPDATE options SET value = 'your_username' WHERE name = 'username'; -- feel free to change 'your_username' to your desired username
UPDATE options SET value = '77/twC5O00cuQgNC63VK32qOKKYwj21ev3jZDXoytVU=' WHERE name = 'passwordVerificationSalt';
UPDATE options SET value = '710BMasZCAgibzIc07X4P9Q4TeBd4ONnqJOho+pWcBM=' WHERE name = 'passwordDerivedKeySalt';
UPDATE options SET value = 'Eb8af1/T57b89lCRuS97tPEl4CwxsAWAU7YNJ77oY+s=' WHERE name = 'passwordVerificationHash';
UPDATE options SET value = 'QpC8XoiYYeqHPtHKRtbNxfTHsk+pEBqVBODYp0FkPBa22tlBBKBMigdLu5GNX8Uu' WHERE name = 'encryptedDataKey';
```

After executing the changes, don't forget to commit/write the changes!

This will set the password to "password". You can use that to login to the application again.

If you already had protected notes (which are not unrecoverable), I recommend deleting them or alternatively export the unprotected notes, delete the document.db and start anew.

If you decide to continue using the existing document file, don't forget to change your password (Options -> Change password).

## Broken note crashes Trilium

Sometimes a particular problem can cause issues for Trilium (e.g. render note with faulty script) and causes Trilium to crash. But since Trilium will normally try to load previously open notes, it will attempt to load again the note, causing the crash again.

To break out of this vicious cycle, you can specify `TRILIUM_START_NOTE_ID` environment variable, which will reset the open tabs to only one with the specified note ID (just use `root`). In linux you could use it like this:

```bash
TRILIUM_START_NOTE_ID=root ./trilium
```

## Sync and consistency checks

Trilium periodically checks logical consistency of the database (e.g. that every note should have a parent). If some inconsistency is detected, the user is notified on the UI about the inconsistency.

In such case, it is recommended to file a bug report and attach anonymized database (see below).

## Broken script prevents application startup

If you experiment with scripting, it might happen that you create a script which crashes the whole Trilium. That's even worse if you set it as a startup script or in an active [[custom widget]].

In such cases you can start Trilium in "safe mode" which will not execute any custom scripts:

```bash
TRILIUM_SAFE_MODE=true ./trilium
```

## Restoring backup

Trilium makes regular automatic backup, so When things go really bad we might need the last option - [[restore backup|Backup#restoring-backup]].

## Reporting bugs

It's a great help to send bug reports. Here are some tips where to look at:

Trilium uses GitHub issues - so please send your reports here: https://github.com/zadam/trilium/issues

**To be clear, the following are not required for each and every bug report, but may be asked for on per-issue basis.**

### Browser console

If Trilium UI is acting up, open developer console by pressing `CTRL-SHIFT-I`, there might be some relevant errors or warnings.

All JavaScript errors should be also logged to backend logs, but it's possible something was missed.

### Backend logs

Trilium logs important events and errors into `logs` directory (inside [[data directory]]). These logs are very helpful in debugging problems, so please attach the latest ones with your bug report. You don't have to worry, they don't contain any sensitive information about your notes.

### Anonymized database

In some cases, it's necessary to see the database structure to be able to debug the problem. Of course, we can't ask you to send us your [[document|Document]] file with your notes.

For this, Trilium supports anonymization of the database - you can trigger this in Options -> Advanced tab.

This will create a copy of your document and remove all sensitive data (currently note titles, contents, revisions, history and some of the options, and non-system attributes) while leaving all structure and metadata (e.g. date of last change). After this is done, the database is [VACUUMed](https://sqlite.org/lang_vacuum.html) to make sure there's no stale sensitive data in the document file. The resulting file is stored in `anonymized` directory (placed in the [[data directory]]). You can safely attach it with your bug report or send it to zadam.apps@gmail.com

#### Command line anonymization

If the database is corrupted in a way which prevents Trilium to start up, you won't be able to trigger the anonymization from the UI. For such a case, anonymization is also available from command line:

```
node src/anonymize.js
```

This needs to be executed in the directory with Trilium source files, for desktop builds this in `resources/app` directory.