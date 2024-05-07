- Layers apply priority to css, regardless of specificity.
- Latest layers are higher priority than former ones.
- No layer is highest priority.
- !important rules are applied backwards.
- @layer creates a sub layer on the "Author origin" layer, which is the layer where stylesheets live. Before that comes the "User origin" layer, not very used and probably to be dropped by chrome, where styles set by the user live. The layer with the least priority is the "User-Agent origin", the browser basically and its default styles.            
- You can define the layers order and then use them in any order you want.

```css
@layer layer-a, layer-b, layer-c;

@layer layer-a {
    /* css here */
}
```
