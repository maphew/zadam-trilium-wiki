Promoted attributes are [[attributes|Attributes]] which are considered important and thus are "promoted" onto main note UI. See example below:

[[images/promoted-attributes.png]]

You can see the note having kind of form with several fields. Each of these is just regular attribute, the only difference is that they appear on the note itself.

Attributes can be pretty useful since they allow for querying and script automation etc. but they are also inconveniently hidden in the note attributes dialog. This allows you to select few of the important ones and push them to the front of the user.

Now, how do we make attribute to appear on the UI?

## Attribute definition

Attribute is always name-value pair where both name and value are strings.

Attribute definition specifies how should this value be interpreted - is it just string, or is it a date? Should we allow multiple values or note?

[[images/attribute-definitions.png]]

In the above picture you can see two labels - tag and todoDate with some values. But below them you can notice again tag and todoDate attributes, but now of type "Label definition". These "definition" attributes define how the "value" attributes should behave.

So there's one attribute for value and one for attribute. But notice how definition attribute is Inheritable, meaning that it's also applied to all descendant note. So in a way, this definition is used for the whole subtree while "value" attributes are applied only for this note.

