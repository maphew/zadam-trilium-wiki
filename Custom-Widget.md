It's possible to create custom widget in three possible locations where you can display your custom content.

Positions are:

* left-pane
* center-pane
* right-pane

## Example

Create a code note of type JS frontend and give it `widget` label.

```javascript
const TPL = `<div></div`;

class TestWidget extends api.TabAwareWidget {
    get position() { return 15; }
    
    get parentWidget() { return 'center-pane'; }
    
    doRender() {
        this.$widget = $(TPL);
        return this.$widget;
    }
    
    async refreshWithNote(note) {
        if (!note.hasOwnedLabel('showTestWidget')) { // show widget only on notes with this label
            this.toggleInt(false); // hide
            
            return;
        }
        
        this.toggleInt(true); // display

        this.$widget.empty().append($("Hello world!"));
    }
}

module.exports = new TestWidget();
```

After you make changes it is necessary to restart Trilium so that the layout can be rebuilt.