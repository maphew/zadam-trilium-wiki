It's possible to create custom widget in three possible locations where you can display your custom content.

Positions are:

*   left-pane
*   center-pane
*   right-pane

## Example - word count widget

Create a code note of type JS frontend and give it `widget` label.

```javascript
/*
 * This defines a custom widget which displays number of words and characters in a current text note.
 * To be activated for a given note, add label 'wordCount' to the note, you can also make it inheritable and thus activate it for the whole subtree.
 * 
 * See it in action in "Books" and its subtree.
 */
const TPL = `<div style="contain: none; padding: 10px; border-top: 1px solid var(--main-border-color);">
    <strong>Word count: </strong>
    <span class="word-count"></span>

    &nbsp;

    <strong>Character count: </strong>
    <span class="character-count"></span>
</div`;

class WordCountWidget extends api.TabAwareWidget {
    get position() { return 100; } // higher value means position towards the bottom/right
    
    get parentWidget() { return 'center-pane'; }
    
    doRender() {
        this.$widget = $(TPL);
        this.$wordCount = this.$widget.find('.word-count');
        this.$characterCount = this.$widget.find('.character-count');
        return this.$widget;
    }
    
    async refreshWithNote(note) {
        if (note.type !== 'text' || !note.hasLabel('wordCount')) { 
            // show widget only on text notes and when marked with 'wordCount' label
            this.toggleInt(false); // hide
            
            return;
        }
        
        this.toggleInt(true); // display
        
        const {content} = await note.getNoteComplement();
        
        const text = $(content).text(); // get plain text only
        
        const counts = this.getCounts(text);

        this.$wordCount.text(counts.words);
        this.$characterCount.text(counts.characters);
    }
    
    getCounts(text) {
        const chunks = text
            .split(/[\s-+:,/\\]+/)
            .filter(chunk => chunk !== '');
        
        let words;
        
        if (chunks.length === 1 && chunks[0] === '') {
            words = 0;
        }
        else {
            words = chunks.length;
        }
        
        const characters = chunks.join('').length;
        
        return {words, characters};
    }
    
    async entitiesReloadedEvent({loadResults}) {
        if (loadResults.isNoteContentReloaded(this.noteId)) {
            this.refresh();
        }
    }
}

module.exports = new WordCountWidget();
```

After you make changes it is necessary to restart Trilium so that the layout can be rebuilt.

### Example screenshot

On the bottom you can see the resulting widget:

![](https://user-images.githubusercontent.com/617641/84592613-4a426e00-ae47-11ea-9d9f-fbe59ac976a1.png)