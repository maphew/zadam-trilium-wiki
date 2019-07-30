Promoted attributes are [[attributes|Attributes]] which are considered important and thus are "promoted" onto main note UI. See example below:

[[images/promoted-attributes.png]]

You can see the note having kind of form with several fields. Each of these is just regular attribute, the only difference is that they appear on the note itself.

Attributes can be pretty useful since they allow for querying and script automation etc. but they are also inconveniently hidden in the note attributes dialog. This allows you to select few of the important ones and push them to the front of the user.

Now, how do we make attribute to appear on the UI?

## Attribute definition

Attribute is always name-value pair where both name and value are strings.

*Attribute definition* specifies how should this value be interpreted - is it just string, or is it a date? Should we allow multiple values or note? And importantly, should we *promote* the attribute or not?

[[images/attribute-definitions.png]]

In the above picture you can see two labels - tag and todoDate with some values. But below them you can notice again tag and todoDate attributes, but now of type "Label definition". These "definition" attributes define how the "value" attributes should behave.

So there's one attribute for value and one for attribute. But notice how definition attribute is [[Inheritable|Attribute inheritance]], meaning that it's also applied to all descendant note. So in a way, this definition is used for the whole subtree while "value" attributes are applied only for this note.

### Inverse relation

Some relations always occur in pairs - my favorite example is on the family. If you have a note representing husband and note representing wife, then there might be a relation between those two of `isPartnerOf`. This is bidirectional relationship - meaning that if a relation is pointing from husband to wife then there should be always another relation pointing from wife to husband.

Another example is with parent - child relationship. Again these always occur in pairs, but in this case it's not exact same relation - the one going from parent to child might be called `isParentOf` and the other one going from child to parent might be called `isChildOf`.

Relation definition allows you to specify such "inverse relation" - for the relation you just define you specify which is the inverse relation. Note that in the second example we should have two relation definitions - one for `isParentOf` which defines `isChildOf` as inverse relation and then second relation definition for `isChildOf` which defines `isParentOf` as inverse relation.

What this does internally is that whenever we save a relation which has defined inverse relation, we check that this inverse relation exists on the relation target note. Similarly when we delete relation, we also delete inverse relation on the target note.
