Trilium supports creating "code" notes, i.e. notes which contain some sort of formal code - be it programming language (C++, JavaScript), structured data (JSON, XML) or other types of codes (CSS etc.).

This can be useful for few things:

* computer programmers can store code snippets as notes
* JavaScript code notes can be executed inside Trilium for some extra functionality
  * we call such JavaScript code notes "scripts"
* JSON, XML etc. can be used as storage for structured data (typically used in conjunction with scripting)

## Scripting

To go further I must explain basic architecture of Trilium - in its essence it is a classic web application - it has these two main components:

* frontend running in the browser (using HTML, CSS, JavaScript) - this is mainly used to interact with the user, display notes etc.
* backend running JavaScript code in node.js runtime - this is responsible for e.g. storing notes, encrypting them etc.

So we have frontend and backend, each with their own set of responsibilities, but their common feature is that they both run JavaScript code. Add to this the fact, that we're able to create JavaScript code notes and we're onto something.

# Button use case

Let's take a look at our demo script (shipped with default Trilium [[document]]) - Task manager. One of the things this script does is adding a button to the Trilium interface which will allow user to easily add new Task (TODO item). 

[[images/button-script.png]]

First take a look at the red point above - this what we want to achieve - new button in UI which will create new note representing a task/todo item.

Red point below the first one marks the note type we have create for this script - it's "JavaScript frontend". It's frontend because adding button to UI is clearly frontend responsibility.

In the note content you can see the code which calls one of the API methods, this one is specifically meant to add new buttons. Code needs to set few button properties:

* button title
* icon which should appear on the button
* optional shortcut under which you can trigger the button
* most importantly "action" - what must happen when button is clicked

## Action handler

Saving the note to the database is backend's responsibility so we immediately pass control to the backend and ask it to create a note. Once this is done, we show the newly created note so that the user can set the task title and maybe some attributes.