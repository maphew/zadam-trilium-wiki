Workspace is a concept built up on top of \[\[note hoisting\]\]. It is based on the idea that a user has several distinct spheres of interest. An example might be "Personal" and "Work", these two spheres are quite distinct and don't interact together. When I focus on Work, I don't really care about personal notes.

So far workspace consists of these features:

*   \[\[note hoisting\]\] - you can "zoom" into a workspace subtree to focus only on the relevant notes
*   easy entering of workspace:

![](https://user-images.githubusercontent.com/617641/107129392-72df1280-68c5-11eb-92b6-6ce1cd52fdff.png)

*   visual identification of workspace in tabs:

![](https://user-images.githubusercontent.com/617641/107129467-d406e600-68c5-11eb-86a7-219f168b47a9.png)

### How to use workspaces

Let's say you have identified the workspaces and their subtrees. Define on the root of this subtree following labels:

*   `#workspace` - just marks this note as workspace, button to enter the workspace is controlled by this
*   `#workspaceIconClass` - controls box icon to be displayed in the tree and tabs, example `bx bx-home`. See [https://boxicons.com/](https://boxicons.com/)
*   `#workspaceTabBackgroundColor` - color of the tab, use any CSS color format, e.g. "lightblue" or "#ddd"
*   `#workspaceCalendarRoot` - marking a note with this label will define a new per-workspace calendar. If there's no such note, global calendar will be used.
