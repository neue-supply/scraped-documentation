# [Working with Styles](https://www.framer.com/developers/styles#working-with-styles)
Styles let you manage text and color appearances from one place in a project. In the UI, you can find them in the Assets panel. Plugins can use these styles to do things like sync design systems or check accessibility.
### [Color Styles](https://www.framer.com/developers/styles#color-styles)
To get or list Color Styles in a project, use the following code.
```
// Lists all Color Styles in a project.
const colorStyles = await framer.getColorStyles()

// Get a specfic Color Style by it's ID.
const colorStyle = await framer.getColorStyle("color-style-id")
```

When creating a new Color Style, the `light` attribute is the default color and used in light theme. The `dark` attribute is an **optional** color used in the dark theme. Colors are stored in RGBA format, e.g `rgba(242, 59, 57, 1)`.
See our lesson on [Light & Dark Mode](https://www.framer.com/academy/lessons/light-dark-mode) to set up a theme toggle within your project.
```
const colorStyle = await framer.createColorStyle({
  name: "My Cool Color",
  light: "rgba(242, 59, 57, 1)",
  dark: "rgba(120, 22, 11, 1)"
})
```

To add the Color Style in a folder, you can set the name and use `/` as a separator. The following example will create a folder called `My Plugin` and add the style inside.
```
const colorStyle = await framer.createColorStyle({
  name: "My Plugin/My Cool Color",
  // ...
})
```

Existing Color Styles can be updated similarly like [Nodes](https://www.framer.com/) by using `setAttributes`.
```
await colorStyle.setAttributes({ dark: "rgba(10, 10, 10, 0.2)" })
```

To remove a Color Style from a project, you'll need to have a reference to the style and call `remove` on it.
```
await colorStyle.remove()
```

You can set data on individual Color Styles. See our guide on the [Plugin Data API](https://www.framer.com/) on how to store data on nodes.
```
await colorStyle.setPluginData("key", "value")
```

### [Text Styles](https://www.framer.com/developers/styles#text-styles)
To get or list Text Styles in a project, use the following code.
```
// Lists all Text Styles in a project.
const textStyle = await framer.getTextStyles()

// Get a specfic Text Style by it's ID.
const textStyle = await framer.getTextStyle("text-style-id")
```

A new Text Style can be added to the project using `createTextStyle`.
```
const textStyle = await framer.createTextStyle({
  name: "Heading,
  tag: "h1",
  fontSize: "30px",
  lineHeight: "1.6em",
})
```

To add the Text Style in a folder, you can set the name and use `/` as a separator. The following example will create a folder called `My Plugin` and add the style inside.
```
const textStyle = await framer.createTextStyle({
  name: "My Plugin/Heading,
  // ...
})
```

Existing Text Styles can be updated similarly like [Nodes](https://www.framer.com/developers/nodes) by using `setAttributes`.
```
const textStyle = await framer.getTextStyle("text-style-id")
if (!textStyle) return

await textStyle.setAttributes({
  // Set the color of the Text Style to red.
  color: "rgba(242, 59, 57, 1)"
})
```

To remove a Text Style from a project, you'll need to have a reference to the style and call `remove` on it.
```
await textStyle.remove()
```

You can set data on individual Text Styles. See our [Plugin Data API ](https://www.framer.com/developers/storing-data)guide on how to store data on nodes.
```
await textStyle.setPluginData("key", "value")
```

#### [Breakpoints](https://www.framer.com/developers/styles#breakpoints)
Text Styles can have variations that apply at different window widths. To add these variations, define overrides using breakpoints.
When defining breakpoints, the main Text Style's attributes will be considered as the largest breakpoint.
The following example defines text that is 16px between 320 and 1024, 18px between 1024 and 1280, and 24px at 1280 and beyond.
```
const textStyle = await framer.createTextStyle({
  fontSize: "24px",
  minWidth: 1280,
  breakpoints: [
    { minWidth: 1024, fontSize: "18px" },
    { minWidth: 320, fontSize: "16px" }
  ]
})
```

A maximum of four breakpoints can be added. An error will be thrown if this limit is exceeded.
Breakpoints will also be automatically ordered from largest to smallest, so the order in which they are defined does not matter. However, each breakpoint must have a unique `minWidth` . If not, an error will be thrown.
```
const textStyle = await framer.createTextStyle({
  minWidth: 1280,
  breakpoints: [
    { minWidth: 320 }
    { minWidth: 1024 },
    { minWidth: 960 },
    { minWidth: 720 },
  ]
})

console.log(textStyle.breakpoints)
// Output:
// [
//   { minWidth: 1024 }, 
//   { minWidth: 960 }, 
//   { minWidth: 720 }, 
//   { minWidth: 320 }
// ]
```

When setting attributes, all attributes except breakpoints will be combined with the existing attributes of the text style. When setting the `breakpoints` attribute, it will override any existing breakpoints the Text Style had.
```
// Make a new Text Style with breakpoints.
const textStyle = await framer.createTextStyle({
  fontSize: "24px",
  minWidth: 1280,
  breakpoints: [
    { minWidth: 1024, fontSize: "18px" },
    { minWidth: 320, fontSize: "16px" }
  ]
})

// Update the created Text Style with new breakpoints.
await textStyle.setAttributes({
  // Only one breakpoint will now exist on the Text Style.
  breakpoints: [
    { minWidth: 320, fontSize: "24px" }
  ]
})
```

To update a breakpoints without overriding them all, you can iterate over the existing breakpoints and merge them.
For example, you may want to scale the font size for all Text Styles and their breakpoints.
```
const textStyles = await framer.getTextStyles()

for (const textStyle of textStyles) {
  await textStyle.set({
    fontSize: parseInt(breakpoint.fontSize) * 0.8 + "px",
    breakpoints: textStyle.breakpoints.map((breakpoint) => {
      return {
        ...breakpoint, 
        fontSize: parseInt(breakpoint.fontSize) * 0.8 + "px"
      }
    })
  })
}
```

By default, text styles will use a built-in font. Use [Fonts](https://www.framer.com/) to customize a Text Style's typeface. Set the `font` attribute when either creating or updating a style.
```
const font = await framer.getFont("Open Sans")
if (!font) return

const textStyle = await framer.createTextStyle({
  font
})
```

Suitable fonts for bold, italic and bold italic variants will automatically be assigned. But these can be overridden for further typographic control.
```
const font = await framer.getFont("Open Sans", { 
  weight: 100 
})

const boldFont = await framer.getFont("Open Sans", {
  weight: 400 
})

const italicFont = await framer.getFont("Open Sans", { 
  weight: 100, 
  style: "italic" 
})

const boldItalicFont = await framer.getFont("Open Sans", { 
  weight: 400,
  style: "italic"
})

if (!font || !boldFont || !italicFont || !boldItalicFont) return

const textStyle = await framer.createTextStyle({
  // Base.
  font,

  // Variants.
  boldFont,
  italicFont,
  boldItalicFont
})
```

All fonts must be part of the same family. For example, Noto Sans Bold can't be used with Inter Regular. An error will be thrown if the families are different.
Fonts can be retrieved from a Text Style like any other attribute.
```
const textStyle = await framer.getTextStyle("text-style-id")

// Log out the family name for the base font.
console.log(textStyle.font.family)

// Font variants may not be defined, check that they exist
// before accessing them.
if (textStyle.boldFont) {
  console.log(textStyle.boldFont.family)
}
```

