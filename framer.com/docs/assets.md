---
title: "Assets"
source: "https://www.framer.com/developers/assets"
domain: "framer.com"
scraped_at: "2025-08-26T16:57:05.970Z"
---
# Assets
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
[Developers](https://www.framer.com/developers/)
![icon entry point for Site Search](https://framerusercontent.com/images/X8K2iCW5Tob8sQuioDPe6TJEU.png)
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
[Developers](https://www.framer.com/developers/)
![icon entry point for Site Search](https://framerusercontent.com/images/X8K2iCW5Tob8sQuioDPe6TJEU.png)
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
# [Working with Styles](https://www.framer.com/developers/assets#working-with-styles)
Styles let you manage text and color appearances from one place in a project. In the UI, you can find them in the Assets panel. Plugins can use these styles to do things like sync design systems or check accessibility.
### [Color Styles](https://www.framer.com/developers/assets#color-styles)
To get or list Color Styles in a project, use the following code.
```
// Lists all Color Styles in a project.
const colorStyles = await framer.getColorStyles()

// Get a specfic Color Style by it's ID.
const colorStyle = await framer.getColorStyle("color-style-id")
```

When creating a new Color Style, the `light` attribute is the default color and used in light theme. The `dark` attribute is an **optional** color used in the dark theme. Colors are stored in RGBA format, e.g `rgba(242, 59, 57, 1)`.
See our lesson on [Light & Dark Mode](https://www.framer.com/academy/lessons/light-dark-mode) to set up a theme toggle within your project.
```javascript
const colorStyle = await framer.createColorStyle({
  name: "My Cool Color",
  light: "rgba(242, 59, 57, 1)",
  dark: "rgba(120, 22, 11, 1)"
})
```

To add the Color Style in a folder, you can set the name and use `/` as a separator. The following example will create a folder called `My Plugin` and add the style inside.
```javascript
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

### [Text Styles](https://www.framer.com/developers/assets#text-styles)
To get or list Text Styles in a project, use the following code.
```
// Lists all Text Styles in a project.
const textStyle = await framer.getTextStyles()

// Get a specfic Text Style by it's ID.
const textStyle = await framer.getTextStyle("text-style-id")
```

A new Text Style can be added to the project using `createTextStyle`.
```javascript
const textStyle = await framer.createTextStyle({
  name: "Heading,
  tag: "h1",
  fontSize: "30px",
  lineHeight: "1.6em",
})
```

To add the Text Style in a folder, you can set the name and use `/` as a separator. The following example will create a folder called `My Plugin` and add the style inside.
```javascript
const textStyle = await framer.createTextStyle({
  name: "My Plugin/Heading,
  // ...
})
```

Existing Text Styles can be updated similarly like [Nodes](https://www.framer.com/developers/nodes) by using `setAttributes`.
```javascript
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

#### [Breakpoints](https://www.framer.com/developers/assets#breakpoints)
Text Styles can have variations that apply at different window widths. To add these variations, define overrides using breakpoints.
When defining breakpoints, the main Text Style's attributes will be considered as the largest breakpoint.
The following example defines text that is 16px between 320 and 1024, 18px between 1024 and 1280, and 24px at 1280 and beyond.
```javascript
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
```javascript
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
```javascript
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

#### [Fonts](https://www.framer.com/developers/assets#fonts)
By default, text styles will use a built-in font. Use [Fonts](https://www.framer.com/) to customize a Text Style's typeface. Set the `font` attribute when either creating or updating a style.
```javascript
const font = await framer.getFont("Open Sans")
if (!font) return

const textStyle = await framer.createTextStyle({
  font
})
```

Suitable fonts for bold, italic and bold italic variants will automatically be assigned. But these can be overridden for further typographic control.
```javascript
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
```javascript
const textStyle = await framer.getTextStyle("text-style-id")

// Log out the family name for the base font.
console.log(textStyle.font.family)

// Font variants may not be defined, check that they exist
// before accessing them.
if (textStyle.boldFont) {
  console.log(textStyle.boldFont.family)
}
```

### [Previous Assets ](https://www.framer.com/developers/assets)### [Next Nodes ](https://www.framer.com/developers/nodes)
### [Previous Assets ](https://www.framer.com/developers/assets)### [Next Nodes ](https://www.framer.com/developers/nodes)
### [Previous Assets ](https://www.framer.com/developers/assets)### [Next Nodes ](https://www.framer.com/developers/nodes)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
---
*Scraped from: https://www.framer.com/developers/assets*