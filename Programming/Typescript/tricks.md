## Use enum values for types

```ts
    export enum DimensionKeys {
      width,
      height,
      'min-width',
      'min-height',
    }

    type DimensionsProps = {
      [key in keyof typeof DimensionKeys]?: string
    }

    console.log(Object.values(DimensionKeys).filter(value => typeof value === "string"))
    // [ "width", "height", "min-width", "min-height" ]
```