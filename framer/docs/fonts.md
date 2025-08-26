# [Working with Fonts](https://www.framer.com/developers/fonts#working-with-fonts)
Plugins can use typefaces available in the Font Picker to get information about specific fonts or to apply them to [Text Styles](https://www.framer.com/#text-styles).
To list all available fonts, use the following code.
```
await framer.getFonts()
```

Unlike the Font Picker, which groups fonts by typeface, `getFonts` will list individual fonts for each weight and style. You can think these as separate font files.
```
// An example snippet from `getFonts`.
[
  //..
  {
    family: "Inter",
    weight: 900,
    style: "normal"
  },
  {
    family: "Noto Sans",
    weight: 400,
    style: "normal"
  },
  {
    family: "Noto Sans",
    weight: 400,
    style: "italic"
  },
  {
    family: "Noto Sans",
    weight: 500,
    style: "normal"
  },
  //..
]
```

To get a specific font from a family, use `getFont` and pass in the family name. This is **not** case sensitive. 
By default, this will return a font in the family that has a normal weight and style.
```
// Get Noto Sans with a weight of 400 in a normal style.
const font = await framer.getFont("Noto Sans")
```

You can specify a desired `weight` or `style` by passing in optional attributes.
```
// Get Noto Sans with a weight of 800 in a normal style.
const font = await framer.getFont("Noto Sans", {
  weight: 800
})

// Get Noto Sans with a weight of 800 in an italic style.
const font = await framer.getFont("Noto Sans", {
  weight: 800,
  style: "italic"
})
```

Make sure to check that a font exists before using it. If a font does not exist, `getFont` will return `null`. 
```
const font = await framer.getFont("General Sans", { weight: 900 })

// Early return if the font does not exist.
if (!font) return

const textStyle = await framer.createTextStyle({ font })
```

This may happen if the typeface is not available in Framer or if it lacks a certain weight and style combination.
> **Note:** Custom fonts are not available to plugins.
