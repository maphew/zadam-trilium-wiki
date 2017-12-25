## Motivation
Trilium's core feature is the ability to structure your notes into hierarchical tree-like structure.

It is expected then that you'll have elaborate and deep note hierarchy - each sub-tree will represent more refined and specialized view of your knowledge base.

This is pretty powerful approach, but it also carries a hidden assumption that each "subtopic" is "owned" by one parent. I'll illustrate this on an example - let's say my basic structure is this:

* Technology
  * Programming
    * Kotlin
    * JavaScript
  * Operating systems
    * Linux
    * Windows
    
Now, I'm starting to learn about [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) and would like to create notes related to this topic. 
But now I'm facing a problem of where to "categorize" this.
The issue here is that Bash is both programming language and tool (shell) very much tied into Linux. It seems it belongs to both of these, I can't (and don't want to) choose one over the other.

## Solution
Solution to the problem shown above is to allow notes to have multiple parents. 

I call these "clones", but it is a bit misleading - there's no original and cloned note - both of these are indistinguishable. 

Another misleading thing about "cloning" is that it suggests that has been made a copy of the note - that's not really true - note itself stays in just one copy, they are just referenced in multiple places in the hierarchy. So of course change in one place affects all other.

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
    
So now the "Bash" subtree appears on multiple locations in the hierarchy.

### Demo
[[gifs/create-clone.gif]]

In the demo, you can see how clone can be created using context menu. It's possible to do this also using Recent notes and Jump to dialogs which is useful in some contexts.

You can also notice how after creating the clone, all clones are highlighted. This is so you can easily see which notes are cloned into other locations in the hierarchy.

When you click on the clone, you can also see in the bottom of the left pane list of all locations of the clone which allows you to switch easily between them.

## Deleting notes/clones

With clones it might not be immediately obvious how deleting works.

If you try to delete a note, it works like this:

1. if the note has multiple clones, delete just this clone and leave the actual note (and its other clones) as it is.
2. if this note doesn't have any other clones, delete the note
   * Run the whole process starting with 1. on all note's children notes 
