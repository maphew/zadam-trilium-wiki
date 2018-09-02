Trilium is currently beta quality software so it's quite expected there will be some bugs.

## General quickfix

You guessed it - it's restart.

If there's a UI problem, it usually means that the Trilium frontend got into inconsistent state and is acting up. Easiest way to fix it is to reload the application - just press `CTRL-R` and frontend will be reloaded.

If this still doesn't help or you suspect it's actually backend issue, you can restart the whole application - in case of desktop (Electron) build, you just close the window and re-open it again.

## Sync and consistency checks

Trilium periodically checks logical consistency of the database (e.g. that every note should have a parent). If some inconsistency is detected, user is notified on the UI about the inconsistency.

In such case, it is recommended to file a bug report and attach anonymized database (see below).

## Reporting bugs

It's a great help to send bug reports. Here are some tips where to look at:

Trilium uses GitHub issues - so please send your reports here: https://github.com/zadam/trilium/issues

**To be clear, following are not required for each and every bug report, but may be asked for on per-issue basis.**

### Browser console

If Trilium UI is acting up, open developer console by pressing `CTRL-SHIFT-I`, there might be some relevant errors or warnings.

All JavaScript errors should be also logged to backend logs, but it's possible something was missed.

### Backend logs

Trilium logs important events and errors into `trilium-data/logs` directory. These logs are very helpful in debugging problems so please attach the latest ones with your bug report. You don't have to worry, they don't contain any sensitive information about your notes.

### Anonymized database

In some cases it's necessary to see the database structure to be able to debug the problem. Of course we can't ask you to send us your [[document|Document]] file with your notes.

For this Trilium supports anonymization of the database - you can trigger this in Settings -> Advanced tab.

This will create a copy of your document and remove all sensitive data (currently note titles and note contents and some of the options) while leaving all structure and metadata (e.g. date of last change). After this is done, database is [VACUUMed](https://sqlite.org/lang_vacuum.html) to make sure there's no stale sensitive data in the document file. Resulting file is stored in `trilium-data/anonymized` directory. You can safely attach it with your bug report.

Note that [[attributes]] are not cleared because they can contain important metadata for debugging.