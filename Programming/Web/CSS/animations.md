## Starting Style
Sets the style when the element becomes displayed, which makes it work with animations and transitions.
```css
@starting-style {
    dialog[open] {

    }
}

dialog[open] {
    @starting-style {
    
    }
}
```

### Interpolate Size
Allows animation with auto sizes. Adding it to root is recommended.
```css
    :root {
        interpolate-size: allow-keywords;
    }
```

### Transition Visibility
Sets the amount of time until the element is visible/invisible.
```css
    div {
        transition: visibility 2s;
    }
```
