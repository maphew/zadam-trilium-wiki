Trilium supports simple backup scheme where it saves copy of the [[document]] on these events:

* once a day
* once a week
* once a month
* before DB migration to newer version

So in total you'll have at most 4 backups from different points in time which should protect you from various problems. These backups are stored by default in `backup` directory placed in the [[data directory]].

This is only very basic backup solution and you're encouraged to add some better backup solution - e.g. backing up the [[document]] to cloud / different computer etc.

Note that [[synchronization]] provides also some backup capabilities by its nature of distributing the data to other computers.

# Restoring backup

Let's assume you want to restore the weekly backup, here's how to do it:

* find [[data directory]] Trilium uses - easy way is to open "About Trilium Notes" from "Menu" in upper left corner and looking at "data directory"
  * I'll refer to `~/trilium-data` as data directory from now on
* find `~/trilium-data/backup/backup-weekly.db` - this is the [[document]] backup
* at this point stop/kill Trilium
* copy and rename this `~/trilium-data/backup/backup-weekly.db` to `~/trilium-data/document.db` - this will delete the current state of the [[document]] so you might want to back it up somewhere else
* start Trilium again

If you have configured sync then you need to do it across all members of the sync cluster, otherwise older version (restored backup) of the document will be detected and synced to the newer version.
