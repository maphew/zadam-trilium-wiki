Family Tree is a [[Script API]] and [[promoted attributes]] showcase present in the [[demo document|Document#demo-document]].

Sometimes it can be difficult to remember all the extended family, relations and birthdays. Trilium notes might be useful in recording these data and possibly visualizing them.

## Demo
[[images/family-tree.png]]

[[images/family-tree-queen.png]]

## Implementation

Members note has `child:template` [[attribute|attributes]] (see [[attribute inheritance]]) defined which means that any note created as a child to Members will have `template` attribute pointing to the `Person template` note (see [[template]]).

This `Person template` defines multiple [[promoted attributes]], some of which (isPartnerOf, isChildOf) allow multiplicity - there can be multiple such relations.

Using these promoted attributes, user can define the whole family tree.

JS [[code note|code notes]] then uses [[Script API]] to pick up all the notes from Members note (pointing to it via `familyContainer` relation), constructs the graph in memory and renders it via 3rd party [Dagre](https://github.com/dagrejs/dagre) JavaScript library which is uploaded (together with its [D3](https://d3js.org/) dependency) as an attachment.