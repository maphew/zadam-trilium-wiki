Every [[attribute|attributes]] has a flag called `isInheritable`. If this is true, then this attribute (key-value) is also applied to all its children notes, children's children notes etc. 

Example how this might be useful is `archived` label which hides its note from Jump to / Add link dialogs. Often times you want to archive some specific subtree, you can do this by making the `archived` label inheritable.

## Copying inheritance

Different kind of inheritance is achieved using `child:` attribute name prefix. If we create a child note in a note with `child:exampleAttribute` attribute, then child note will have `exampleAttribute` created. This can be even chained, e.g. `child:child:exampleAttribute`, in this case `exampleAttribute` will be created in the child of the child.

Which kind of attribute inheritance (or if any at all) should be used depends on specific use case.

## Template inheritance

[[Attribute template|template]] could be also seen as a form of inheritance.
