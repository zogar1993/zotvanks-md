### Do as many columns in a grid as possible

```css
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

### Do columns without a grid or table
These columns will fill the content one column at a time, instead of filling one row at a time.

```css
columns: <column-width> <column-count>;
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

### Adjusting dynamically to viewport size

```css
font-size: clamp(1rem, 10vw, 2rem);
```

### Making paragraphs wrap better visually

```css
/* works well for long paragraphs */
text-wrap: pretty;

/* works well for 3 lines or so paragraphs */
text-wrap: balanced;
```

### Change list items icon

```css
@counter-style circled-alpha {
  system: fixed;
  symbols: Ⓐ Ⓑ Ⓒ Ⓓ Ⓔ Ⓕ Ⓖ Ⓗ Ⓘ Ⓙ Ⓚ Ⓛ Ⓜ Ⓝ Ⓞ Ⓟ Ⓠ Ⓡ Ⓢ Ⓣ Ⓤ Ⓥ Ⓦ Ⓧ Ⓨ Ⓩ;
  suffix: " ";
}

.items {
  list-style: circled-alpha;
}
```

### Style area behind the element, useful for glass effect

```css
backdrop-filter: blur(2px);
```

### Add css only if the user has hover capabilities

```css
@media (hover) {

}
```

### Setting a max width in columns with fit-content

```css
grid-template-columns: 200px fit-content(40ch) 1fr;
```

### Making an image which you don't care it will be shown completely, but you want to make it show on dynamic aspect ratios without distorting the image

```css
object-fit: cover;
```

### Setting scrims on top of images

```css
border-image: fill 0 linear-gradient(#0003, #000);
```

### Mixing colors

```css
color: color-mix(in srgb, orange 20%, blue);

color: rgb(from var(--color) calc(r + 50) calc(g * .5) var(--some-color));
```

### Form inputs showing valid or invalid state

```css
  /* these just kick in after user interacts with input */
  input:user-valid
  input:user-invalid

  /* hack for older browsers */
  input:not(:placeholder-shown):valid
  input:not(:placeholder-shown):invalid

  /* target input while being edited, but is still invalid */
  input:focus:invalid
```

### Links
- [Auto Dimension Transitions](https://css-tricks.com/using-css-transitions-auto-dimensions/): When you want to collapse and expand with a transition.
- [CSS Positions](https://zellwk.com/blog/css-positions/): Explanations for css positions static, relative, absolute and fixed (but not sticky).