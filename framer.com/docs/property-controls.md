---
title: "Property Controls"
source: "https://www.framer.com/developers/property-controls"
domain: "framer.com"
scraped_at: "2025-08-26T17:04:26.019Z"
---
# Property Controls
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
# [Property Controls](https://www.framer.com/developers/property-controls#property-controls)
Property Controls allow users to pass properties (or props) to a code component through the Framer interface. When a user selects a code component on the canvas, its Property Controls are visible on the properties panel. As a component author, it’s up to you to decide which Property Controls to add and what options they should present to the user.
### [Adding Controls](https://www.framer.com/developers/property-controls#adding-controls)
To give your component Property Controls, import both the `addPropertyControls` function and the `ControlType` type from the `framer` library.
Below your component, call the `addPropertyControls` function with two arguments: first, the name of your component; and second, an object that defines controls for different properties. You have several types of controls to choose from, each of which are documented on this page.
Property Controls only affect components on the canvas. For this reason, you'll still want to use `defaultProps` for your component’s props, both to prevent errors as you code the component and when a designer creates an instance of your component from code.
In this example, we’re adding a Property Control for our component’s `text` prop. On the canvas, selecting the component will now display a control that allows us to set this property.
```python
import { addPropertyControls, ControlType } from "framer"

export function MyComponent(props) {
  return <div>{props.text}</div>
}

MyComponent.defaultProps = {
  text: "Hello World!",
}

addPropertyControls(MyComponent, {
  text: { type: ControlType.String, title: "Hello World" },
})
```

### [Hiding Controls](https://www.framer.com/developers/property-controls#hiding-controls)
Controls can be hidden by adding the `hidden` function to the property description. The function receives an object containing the set properties and returns a `boolean`. In this example, we hide the `text` property entirely when the connected property (the `toggle`) is `false`. Now you can toggle the visibility of the text property control by changing the `toggle` boolean from within the property panel in Framer.
```
export function MyComponent(props) {
  return <div>{props.text}</div>
}

MyComponent.defaultProps = {
  text: "Hello World!",
  toggle: true,
}

addPropertyControls(MyComponent, {
  toggle: {
    type: ControlType.Boolean,
    title: "Toggle",
    enabledTitle: "Show",
    disabledTitle: "Hide",
  },
  text: {
    type: ControlType.String,
    title: "Text",
    hidden(props) {
      return props.toggle === false
    },
  },
})

```

### [Adding Descriptions](https://www.framer.com/developers/property-controls#adding-descriptions)
Controls can have a `description` property to add documentation about the control in the Framer UI—it appears in the Properties panel just above the control. It also supports adding emphasis and links using Markdown syntax. To add line breaks, use the newline character “`\n`”.
```
export function MyComponent(props) {
  return <div>{props.text}</div>
}

MyComponent.defaultProps = {
  text: "Hello World!",
  toggle: true,
}

addPropertyControls(MyComponent, {
  toggle: {
    type: ControlType.Boolean,
    title: "Toggle",
    description: "*On* by default",
  },
  text: {
    type: ControlType.String,
    title: "Text",
    description: "[Need inspiration?](https://www.lipsum.com)",
  },
})
```

### [Controls](https://www.framer.com/developers/property-controls#controls)
#### [Array `ControlType.Array`](https://www.framer.com/developers/property-controls#array-controltype-array)
A control that allows multiple values per `ControlType`, provided as an array via properties. For most control types this will be displayed as an additional section in the properties panel allowing as many fields to be provided as required.
For a `ControlType.ComponentInstance`, the component will also gain an additional outlet control on the Canvas that allows links to be created between frames.
Group properties together by using an object control.
```
export function MyComponent(props) {
  const frames = props.images.map(image => {
    return <img src={image} style={{ width: 50, height: 50 }} />
  })
  
  return <div style={{ display: "flex", gap: 10 }}>{frames}</div>
}

// Add a repeatable image property control
addPropertyControls(MyComponent, {
  images: {
    type: ControlType.Array,
    control: {
      type: ControlType.Image
    },
    // Allow up to five items
    maxCount: 5,
  },
})

// Add a multi-connector to your component to connect components on the canvas
addPropertyControls(MyComponent, {
  children: {
    type: ControlType.Array,
    control: {
      type: ControlType.ComponentInstance
    },
    maxCount: 5,
  },
})

// Add a list of objects
addPropertyControls(MyComponent, {
  myArray: {
    type: ControlType.Array,
    control: {
      type: ControlType.Object,
      controls: {
        title: { type: ControlType.String, defaultValue: "Employee" },
        avatar: { type: ControlType.Image },
      },
    },
    defaultValue: [
      { title: "Jorn" },
      { title: "Koen" },
    ],
  },
})

// For multiple values, you can pass in an array of single values as the React default prop.
MyComponent.defaultProps = {
   paddings: [5, 10, 15],
}
```

#### [Boolean `ControlType.Boolean`](https://www.framer.com/developers/property-controls#boolean-controltype-boolean)
A control that displays an on / off checkbox. The associated property will be `true` or `false` , depending on the state of the checkbox. Includes an optional `defaultValue`, which is set to `true` by default.
```
export function MyComponent(props) {
    return (
        <div style={{ minHeight: 50, minWidth: 50 }}>
            {props.showText ? "Hello World" : null}
        </div>
    )
}

addPropertyControls(MyComponent, {
  showText: {
    type: ControlType.Boolean,
    title: "Show Text",
    defaultValue: true,
  },
})
```

#### [Color `ControlType.Color`](https://www.framer.com/developers/property-controls#color-controltype-color)
A control that represents a color value. It will be included in the component props as a string.
This control is displayed as a color field and will provide the selected color in either RGB (`rgb(255, 255, 255)`) or RGBA `(rgba(255, 255, 255, 0.5)` notation, depending on whether there is an alpha channel.
You can also make the color optional by adding the optional property.
```
export function MyComponent(props) {
  return (
    <div
      style={{
        backgroundColor: props.background,
        width: 50,
        height: 50,
      }}
    />
  )
}

addPropertyControls(MyComponent, {
  background: {
    type: ControlType.Color,
    defaultValue: "#fff",
    optional: true,
  },
})
```

#### [ComponentInstance `ControlType.ComponentInstance`](https://www.framer.com/developers/property-controls#componentinstance-controltype-componentinstance)
A control that references to another component on the canvas, included in the component props as a React node. The component will have an outlet to allow linking to other Frames. Available Frames will also be displayed in a dropdown menu in the properties panel. The component reference will be provided as a property. As a convention, the name for the property is usually just `children`.
Multiple components can be linked by combining the `ComponentInstance` type with the `ControlType.Array[](https://www.framer.com/#array-controltype-array)`.
```
export function MyComponent(props) {
  return <div>{props.children}</div>
}

addPropertyControls(MyComponent, {
  children: {
    type: ControlType.ComponentInstance,
  },
})
```

#### [Date `ControlType.Date`](https://www.framer.com/developers/property-controls#date-controltype-date)
A property control that represents a date. The date will be passed in as an ISO 8601 formatted string.
```
export function MyComponent(props) {
  return <div>{props.date}</div>
}

addPropertyControls(MyComponent, {
    date: {
        type: ControlType.Date,
        title: "Date"
    },
})
```

#### [Enum `ControlType.Enum`](https://www.framer.com/developers/property-controls#enum-controltype-enum)
A property control that represents a list of options. The list contains primitive values and each value has to be unique. The selected option will be provided as a property. This control is displayed as a dropdown menu in which a user can select one of the items. `displaySegmentedControl` can be enabled to display a segmented control instead.
**Note:**`ControlType.SegmentedEnum` is deprecated, please use `ControlType.Enum` and enable `displaySegmentedControl`.
```
export function MyComponent(props) {
  const value = props.value || "a"
  const colors = { a: "red", b: "green", c: "blue" }
  return (
    <div 
      style={{ 
        backgroundColor: colors[value], 
        width: 50, 
        height: 50 
      }}
    >
      {value}
    </div>
  )
}

addPropertyControls(MyComponent, {
  value: {
    type: ControlType.Enum,
    defaultValue: "a",
    displaySegmentedControl: true,
    segmentedControlDirection: "vertical",
    options: ["a", "b", "c"],
    optionTitles: ["Option A", "Option B", "Option C"]
  },
})
```

#### [EventHandler `ControlType.EventHandler`](https://www.framer.com/developers/property-controls#eventhandler-controltype-eventhandler)
A control that exposes events in the Interactions section of the Properties Panel when used within Smart Components.When selection Interactions such as “New Transition”, you can select which event to listen to.
```
export function MyComponent(props) {
  return <motion.div onTap={props.onTap} style={{ width: 50, height: 50 }} />
}

addPropertyControls(MyComponent, {
  onTap: {
    type: ControlType.EventHandler,
  },
})
```

#### [File `ControlType.File`](https://www.framer.com/developers/property-controls#file-controltype-file)
A control that allows the user to pick a file resource. It will be included in the component props as a URL string. Displayed as a file picker that will open a native file browser. The selected file will be provided as a fully qualified URL. The `allowedFileTypes` property must be provided to specify acceptable file types.
```
export function MyComponent(props) {
  return (
      <video
        style={{ objectFit: "contain", ...props.style }}
        src={props.filepath}
        controls
      />
  )
}

addPropertyControls(MyComponent, {
  filepath: {
    type: ControlType.File,
    allowedFileTypes: ["mov"],
  },
})
```

#### [ResponsiveImage `ControlType.ResponsiveImage`](https://www.framer.com/developers/property-controls#responsiveimage-controltype-responsiveimage)
A control that allows the user to pick an image resource. Displayed as an image picker with associated file picker.
The chosen image will be provided in the component props as an object with `src` and `srcSet` properties:
  * `src`: a string containing the URL of a full resolution image
  * `srcSet`: an optional string with scaled down image variants. This is typically passed into `<img srcSet />[](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/srcset)` and helps the browser to load a smaller image when a full-size one isn’t necessary.
  * `alt`: an optional description of the image.

**Note:** `ControlType.Image` is deprecated, please use `ControlType.ResponsiveImage`
```
export function MyComponent(props) {
  return (
      <img 
        src={props.image.src}
        srcSet={props.image.srcSet}
        alt={props.image.alt}
      />
  )
}
     
addPropertyControls(MyComponent, {
  image: {
    type: ControlType.ResponsiveImage,
  }
})
```

#### [Number `ControlType.Number`](https://www.framer.com/developers/property-controls#number-controltype-number)
A control that accepts any numeric value. This will be provided directly as a property. Will display an input field with a range slider by default. The `displayStepper` option can be enabled to include a stepper control instead.
```python
import { motion } from "framer-motion"

export function MyComponent(props) {
    return (
        <motion.div rotateZ={props.rotation} style={{ width: 50, height: 50 }}>
            {props.rotation}
        </motion.div>
    )
}

addPropertyControls(MyComponent, {
  rotation: {
    type: ControlType.Number,
    defaultValue: 0,
    min: 0,
    max: 360,
    unit: "deg",
    step: 0.1,
    displayStepper: true,
  },
})
```

#### [Object `ControlType.Object`](https://www.framer.com/developers/property-controls#object-controltype-object)
A control that allows for grouping multiple properties as an object.
You can make the object removable by adding the optional property. To replace the default button title, use the `buttonTitle` property. To change the default icon, use the `icon` property.
```
export function MyComponent(props) {
  return (
    <div 
      style={{ 
        opacity: props.myObject.opacity,
        backgroundColor: props.myObject.tint
      }} 
    />
  )
}

addPropertyControls(MyComponent, {
  optional: true,
  buttonTitle: "Style",
  icon: "color", // boolean, object, color, effect or interact
  myObject: {
    type: ControlType.Object,
    controls: {
      opacity: { type: ControlType.Number },
      tint: { type: ControlType.Color },
    }
  }
})
```

#### [String `ControlType.String`](https://www.framer.com/developers/property-controls#string-controltype-string)
A control that accepts plain text values. This will be provided directly as a property. Will display an input field with an optional placeholder value.
If `obscured` attribute is set to true a password input field will be used instead of a regular text input so that the value in the input will be visually obscured, yet still be available as plain text inside the component. `displayTextArea` can be enabled to display a multi-line input area instead. `maxLength` can be set to limit the maximum number of characters that can be entered in the input field.
```
export function MyComponent(props) {
  return <div>{props.title} — {props.body}</div>
}

addPropertyControls(MyComponent, {
  title: {
    type: ControlType.String,
    defaultValue: "Framer",
    placeholder: "Type something…",
    maxLength: 50
  },
  body: {
    type: ControlType.String,
    defaultValue: "Lorem ipsum dolor sit amet.",
    placeholder: "Type something…",
    displayTextArea: true,
  },
})
```

#### [Transition `ControlType.Transition`](https://www.framer.com/developers/property-controls#transition-controltype-transition)
A control that allows for editing Framer Motion transition options within the Framer UI.
```
export function MyComponent(props) {
  return (
      <motion.div
         animate={{ scale: 2 }}
         transition={props.transition}
      />
  )
}

addPropertyControls(MyComponent, {
  transition: {
    type: ControlType.Transition,
    defaultValue: { type: "spring", stiffness: 800, damping: 60 },
  },
})
```

#### [Link `ControlType.Link`](https://www.framer.com/developers/property-controls#link-controltype-link)
A control that allows for exposing web links.
```
export function MyComponent(props) {
  return <a href={props.link}>My Link</a>
}

addPropertyControls(MyComponent, {
  link: {
    type: ControlType.Link,
    defaultValue: "https://www.framer.com"
  }
})
```

#### [Padding `ControlType.Padding`](https://www.framer.com/developers/property-controls#padding-controltype-padding)
A control that represents CSS padding. Will display an input field to accept a single value, alongside a segmented control allowing four distinct values to be provided.
Includes an optional `defaultValue` that can be set with single value (e.g. `"10px"` or `"10px 20px 30px 40px"`).
**Note:** `FusedNumber` is deprecated, please use `ControlType.Padding[](https://www.framer.com/#padding-controltype-padding)` and `ControlType.BorderRadius[](https://www.framer.com/#borderradius-controltype-borderradius)`
```
export function MyComponent({ padding }) {
  return <div style={{ padding }} />
}
     
addPropertyControls(MyComponent, {
  padding: {
    type: ControlType.Padding,
    defaultValue: "8px",
  }
})
```

#### [BorderRadius `ControlType.BorderRadius`](https://www.framer.com/developers/property-controls#borderradius-controltype-borderradius)
A control that represents CSS border radius. Will display an input field to accept a single value, alongside a segmented control allowing four distinct values to be provided.
Includes an optional `defaultValue` that can be set with single value (e.g. `"10px"` or `"10px 20px 30px 40px"`).
**Note:** `FusedNumber` is deprecated, please use `ControlType.Padding[](https://www.framer.com/#padding-controltype-padding)` and `ControlType.BorderRadius[](https://www.framer.com/#borderradius-controltype-borderradius)`
```
export function MyComponent({ borderRadius }) {
  return <div style={{ borderRadius }} />
}
     
addPropertyControls(MyComponent, {
  borderRadius: {
    type: ControlType.BorderRadius,
    defaultValue: "16px",
    title: "Radius",
  }
})
```

#### [Border `ControlType.Border`](https://www.framer.com/developers/property-controls#border-controltype-border)
A control that represents a border style. Either `borderWidth` or the equivalent per-side values (e.g `borderTopWidth`, `borderLeftWidth`, `borderRightWidth`, `borderBottomWidth`) will be provided.
```
export function MyComponent(props) {
  return <div style={props.border} />
}

addPropertyControls(MyComponent, {
  border: {
    type: ControlType.Border,
    defaultValue: {
      borderWidth: 1,
      borderStyle: "solid", // solid, dashed, dotted or double
      borderColor: "rgba(0, 0, 0, 0.5)",
    },
  }
})
```

You can also set the default value for each side.
```
export function MyComponent(props) {
  return <div style={props.border} />
}

addPropertyControls(MyComponent, {
  border: {
    type: ControlType.Border,
    defaultValue: {
      borderTopWidth: 2,
      borderRightWidth: 1,
      borderBottomWidth: 2,
      borderLeftWidth: 1,
      borderStyle: "solid", // solid, dashed, dotted or double
      borderColor: "rgba(0, 0, 0, 0.5)",
    },
  }
})
```

#### [BoxShadow `ControlType.BoxShadow`](https://www.framer.com/developers/property-controls#boxshadow-controltype-boxshadow)
A control that allows for exposing shadows. The value will be provided as a string with valid CSS box-shadow values.
```
export function MyComponent(props) {
  return <motion.div style={{boxShadow: props.shadow}} />
}

addPropertyControls(MyComponent, {
  shadow: {
    type: ControlType.BoxShadow,
    defaultValue: "0px 1px 2px 0px rgba(0,0,0,0.25)",
  }
})
```

### [Previous Auto-Sizing ](https://www.framer.com/developers/auto-sizing)### [Next Reference ](https://www.framer.com/developers/components-reference)
### [Previous Auto-Sizing ](https://www.framer.com/developers/auto-sizing)### [Next Reference ](https://www.framer.com/developers/components-reference)
### [Previous Auto-Sizing ](https://www.framer.com/developers/auto-sizing)### [Next Reference ](https://www.framer.com/developers/components-reference)
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
*Scraped from: https://www.framer.com/developers/property-controls*