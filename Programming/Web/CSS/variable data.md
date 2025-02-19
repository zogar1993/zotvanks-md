## Variables

```css
--this-is-a-variable: 20px;
padding: var(--this-is-a-variable);
```
## Attribute

```html
<div data-this-attribute="smt" />
```

```css
div[data-this-attribute]:before {
    content: attr(data-this-attribute);
}
```

## Counters

```css
ol {
    counter-reset: counter-name;
}

li:before {
    counter-increment: counter-name;
    content: counter(counter-name) ' ';
}
```

## Properties

```css
@property --pink {
    syntax: '<color>';
    inherits: false;
    initial-value: hotpink;
}
```