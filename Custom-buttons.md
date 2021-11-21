You can create custom buttons that run your frontend code, and assign shortcuts to them. The default database has an example of a button that opens today's page:

```javascript
api.addButtonToToolbar({
    title: 'Today',
    icon: 'calendar',
    shortcut: 'alt+t',
    action: async function() {
        const todayNote = await api.getTodayNote();

        await api.waitUntilSynced();
        
        api.activateNote(todayNote.noteId);
    }
});
```

You can add the button to Trilium by creating a note of type "JS frontend" with this code.

To add the button on startup of the "desktop frontend", add a `#run=frontendStartup` attribute.

To add the button into the "mobile frontend", add `#run=mobileStartup`.