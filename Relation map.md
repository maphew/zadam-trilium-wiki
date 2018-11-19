Relation map is a type of [[Tree concepts#note|note]] which visualizes notes and their [[Attributes|relations]]. See an example:

[[images/relation-map.png]]

## Usage

First take a look at the demo:

[[gifs/relation-map-demo.gif]]

There are several steps here:

* we start with empty relation map and two existing notes representing Prince Philip and Queen Elizabeth II. These two notes already have "isPartnerOf" [[attributes|relations]] defined.
  * There are actually two "inverse" relations (one from Philip to Elizabeth and one from Elizabeth to Philip) 
* we drag both notes to relation map and place to suitable position. Notice how the existing "isPartnerOf" relations are displayed.
* now we create new note - we name it "Prince Charles" and place it on the relation map by clicking on the desired position. The note is by default created under the relation map note (visible in the note tree on the left).
* we create two new relations "isChildOf" targeting both Philip and Elizabeth
  * now there's something unexpected - we can also see the relation to display another "hasChild" relation. This is because there's a [[Promoted attributes|relation definition]] which puts "isChildOf" as an "[[Promoted attributes#Inverse relation|inverse]]" relation of "hasChildOf" (and vice versa) and thus it is created automatically.
* we create another note for Princess Diana and create "isPartnerOf" relation from Charles. Again notice how the relation has arrows both ways - this is because "isPartnerOf" definition specifies its inverse relation as again "isPartnerOf" so the opposite relation is created automatically.
* as the last step we pan & zoom the map to fit better to window dimensions.

Relation definitions mentioned above come from "Person template" note which is assigned to any child of "My Family Tree" relation note. You can play with the whole thing in the [[Document#Demo document|demo document]].