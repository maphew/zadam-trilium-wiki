# Mac OS support

Originally, desktop builds of Trilium Notes has been available for Windows & Linux, 
but there has been a considerable demand for Mac OS build. 

So I made one, but I underestimated the differences and specifics of Mac platform which seems 
to require special handling in several places. My lack of knowledge and frankly 
willingness to learn & code Mac specific functionality resulted in a current state 
where [Trilium does not integrate well into the OS](https://github.com/zadam/trilium/issues/511).

Mac OS build is from now on considered "unsupported". I will strive to keep it fundamentally functional, 
but I won't work on Mac specific features or integrations.
Note that this is more of an acknowledgment of an existing state rather than sudden change of direction.

Of course, PRs are welcome.

# Why database instead of flat files?

Trilium stores notes in a [[document]] which is an SQLite database. People often ask why doesn't Trilium rather use flat files
for note storage - it's fair question since flat files are easily interoperable, work with SCM/git etc.

Short answer is that file systems are simply not powerful enough for what we want to achieve with Trilium. Using filesystem would mean less features with probably more problems.

More detailed answer:

* [[clones|cloning notes]] are what you might call "hard directory link" in filesystem lingo, but this concept is not implemented in any filesystem
* filesystems make a distinction between directory and file while there's intentionally no such difference in Trilium
* Trilium allows storing note [[attributes]] which could be represented in extended user attributes but their support differs greatly among different filesystems / operating systems
* Trilium makes links / relations between different notes which can be quickly retrieved / navigated (e.g. for [[link map]]). There's no such support in file systems which means these would have to be stored in some kind of side car files (mini-databases).
* Filesystems are generally not transactional. While this is not completely required for a note taking application, having transactions make it way easier to keep notes and their metadata in predictable and consistent state.
