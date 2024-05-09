### Do as many columns in a grid as possible

```css
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

### How to do columns without a grid or table
These columns will fill the content one column at a time, instead of filling one row at a time.

```css
columns: <column-width> <column-count>;
```