### Rlements not affected by classes

```css
a:not([class])
```

### Range of elements
```css
/* from 7 to 0 */
li:nth-child(n + 7):nth-child(-n + 9)
```

### All but the one hovered
```css
/* "select from the parent" way */
.showcase:hover img { /* ones not hovered */ }
.showcase img:hover { /* one hovered */ }

/* "all in one selector" way */
.showcase:has(img:hover) img:not(:hover) { /* ones not hovered */}
```

### Surrounding elements 
```css
/* select next */
 li:hover + li

/* select previous */
 li:has(+ :hover)

/* select all that come after */
 li:hover ~ li

/* select all that come before */
 li:has(~ :hover)
```

### Element with no children

```css
div:empty
```

### :focus vs :focus-visible

```css
/* applies when clicked or focused by keyboard navigation */
div:focus

/* usually the one you want to use */
/* applies only when focused by keyboard navigation */
div:focus-within
```

### Element that has a focused child

```css
div:focus-within
```
