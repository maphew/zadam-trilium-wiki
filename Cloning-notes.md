## Motivation
Trilium's core feature is the ability to structure your notes into hierarchical tree-like structure.

It is expected then that you'll have an elaborate and deep note hierarchy - each sub-tree will represent a more refined and specialized view of your knowledge base.

This is a pretty powerful approach, but it also carries a hidden assumption that each "subtopic" is "owned" by one parent. I'll illustrate this with an example - let's say my basic structure is this:

* Technology
  * Programming
    * Kotlin
    * JavaScript
  * Operating systems
    * Linux
    * Windows
    
Now, I'm starting to learn about [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) and would like to create notes related to this topic. But now I'm facing a problem of where to "categorize" this. The issue here is that Bash is both a programming language and a tool (shell) very much tied into Linux. It seems it belongs to both of these, I can't (and don't want to) choose one over the other.

## Solution
The solution to the problem shown above is to allow notes to have multiple parents. 

I call these "clones", but that is a bit misleading - there's no original and cloned note - the notes in both of the parents categories are identical. 

Another misleading thing about "cloning" is that it suggests that a copy of the note has been made. That's not really true, the note itself stays in just one file, but they are just referenced in multiple places in the note hierarchy. So changing it in one category changes it in all the others, because they're all the same file.
Here's the final structure with cloning:

* Technology
  * Programming
    * Kotlin
    * JavaScript
    * Bash
      * some subnotes ...
  * Operating systems
    * Linux
      * Bash
        * some subnotes ...
    * Windows
    
So now the "Bash" sub-tree appears on multiple locations in the hierarchy. Both the Bash sub-trees are the same and contain the same sub-categories and notes.

### Demo
[[gifs/create-clone.gif]]

In the demo, you can see how a clone can be created using the context menu. It's possible to do this also using the Add Link dialog or with CTRL+C and CTRL+V [[shortcuts|keyboard shortcuts]].

You can also notice how after creating the clone, all clones are highlighted. This is so you can easily see which notes are cloned into other locations in the hierarchy.

Please note: in more recent versions, titles of cloned notes in the tree view have an asterisk to the right. The location for finding the clones within a category has also been changed to a drop-down menu that you can find at the top of the category tree-view when you've selected a cloned category. The reason for this change is documented in [issue 1139](https://github.com/zadam/trilium/issues/1139#issuecomment-651582746).

![Example of finding new cloned category paths](https://user-images.githubusercontent.com/617641/86092919-7c420a00-baae-11ea-93dd-f7abbc9125b6.png)

## Prefix

Since notes can be categorized into multiple places, it's recommended to choose a generalized name that fits into all locations instead of something more specific to avoid confusion. In some cases this isn't possible so Trilium provides "branch prefixes", which is shown before the note name in the tree and as such provides a specific kind of context. The prefix is location specific so it's displayed only in the tree pane.

## Deleting notes/clones

With clones it might not be immediately obvious how deleting works.

If you try to delete a note, it works like this:

1. if the note has multiple clones, delete just this clone and leave the actual note (and its other clones) as it is.
2. if this note doesn't have any other clones, delete the note
   * Run the whole process starting with 1. on all note's children notes 
