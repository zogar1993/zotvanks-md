### Do as many columns in a grid as possible

```css
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

### Do columns without a grid or table
These columns will fill the content one column at a time, instead of filling one row at a time.

```css
columns: <column-width> <column-count>;
```

### Select elements not affected by classes

```css
a:not([class])
```

### Select range of elements
```css
/* from 7 to 0 */
li:nth-child(n + 7):nth-child(-n + 9)
```

### Style all but the one hovered
```css
/* "select from the parent" way */
.showcase:hover img { /* ones not hovered */ }
.showcase img:hover { /* one hovered */ }

/* "all in one selector" way */
.showcase:has(img:hover) img:not(:hover) { /* ones not hovered */}
```

### Select surrounding elements 
```css
/* select next */
 li:hover + li

/* select previous */
 li:has(+ :hover)

/* select all that come next */
 li:hover ~ li

/* select all that come previous */
 li:has(+ :hover)
```

### Keep theming content all in one place with nesting
```css
 .button {
    /* button css */
    .dark-theme & {
        /* dark button css */
    }
 }
```

### Vertically align content without flex or grid
```css
 align-content: center;
```

### Use minimum width for flex children
```css
 min-width: fit-content;
```

### Use conditionally on browser support
```css
@supports (display: flex) {
  .flex-container > * {
    text-shadow: 0 0 2px blue;
    float: none;
  }

  .flex-container {
    display: flex;
  }
}
```