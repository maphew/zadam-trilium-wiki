Every [[attribute|attributes]] has a flag called `isInheritable`. If this is true, then this attribute (key-value) is also applied to all its children notes, children's children notes etc.

## Copying inheritance

Different kind of inheritance is achieved using "child:" attribute name prefix. If we create a child note in a note with "child:exampleAttribute" attribute, then child note will have "exampleAttribute" created. This can be even chained, e.g. "child:child:exampleAttribute", in this case "exampleAttribute" will be created in the child of the child.

Which kind of attribute inheritance (or if any at all) should be used depends on specific use case.