## Number inputs have issues

- The first has validation issues and you may need to remove arrows from it.
- The second does not have arrow modifications.
- We add inputmode="numeric" on both since that way mobile shows numeric keyboard instead of full text keyboard.

```html
<input type="number" inputmode="numeric"/>
<input type="text" pattern="[0-9]+" inputmode="numeric">
```

## Color input

```html
<input type="color"/>
```
