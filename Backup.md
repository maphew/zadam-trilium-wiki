Trilium supports simple backup scheme where it saves copy of the [[document]] on these events:

* once a day
* once a week
* once a month
* before DB migration to newer version

So in total you'll have at most 4 backups from different points in time which should protect you from various problems. These backups are stored by default in `backup` directory placed in the [[data directory]].

This is only very basic backup solution and you're encouraged to add some better backup solution - e.g. backing up the [[document]] to cloud / different computer etc.

Note that [[synchronization]] provides also some backup capabilities by its nature of distributing the data to other computers.