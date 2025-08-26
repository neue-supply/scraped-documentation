# [API Reference](https://www.framer.com/developers/components-reference#api-reference)
A list of exports from the `framer` library available in every Code Component.
## [RenderTarget](https://www.framer.com/developers/components-reference#rendertarget)
To detect which context your Code Component is currently being shown, you can import and use `RenderTarget`. This includes `RenderTarget.current()` function to check the current RenderTarget as well as few types to check them against.
  * `RenderTarget.canvas` — The Canvas
  * `RenderTarget.export` — The Export Canvas
  * `RenderTarget.thumbnail` — Project Thumbnails
  * `RenderTarget.preview` — The Preview or live site


```
import { RenderTarget } from "framer"

const isOnCanvas = RenderTarget.current() === RenderTarget.canvas
```

#### [Canvas and Export](https://www.framer.com/developers/components-reference#canvas-and-export)
For Components that animate, like WebGL shaders, we have a custom hook that we recommend you use instead. This ensures that your Component is static both on the Canvas and the exported assets—preventing performance issues on the Canvas and exporting issues like tiling, which are issues caused by the Component still animating during export. For all animated components, instead of `RenderTarget`, use this hook.
```
import { useIsStaticRenderer } from "framer"

// Static on both Canvas and Export
const isStaticRenderer = useIsStaticRenderer()
```

## [Localization](https://www.framer.com/developers/components-reference#localization)
When using Localization with Framer you may want to create a custom Locale Picker. In most cases you should do this with Smart Components, which you can learn about in the [Localization 2.0 video](https://youtu.be/5ZQ2-w1KwGo?feature=shared&t=250). However if you have very specific needs based on logic there is an API for getting and setting the current Locale info.
##### [`useLocaleInfo()`](https://www.framer.com/developers/components-reference#uselocaleinfo\(\))
```
const { activeLocale, locales, setLocale } = useLocaleInfo()

function handleChange(event) {
    const locale = locales.find((locale) => locale.id === localeId)
    setLocale(locale)
}

return (
  select
    value={activeLocale?.id ?? "default"}
    onChange={handleChange}
  
    {locales.map((locale) => (
      option key={locale.id} value={locale.id}
        {locale.name}
      </option
    ))}
  </select
)
```

## [Property Controls](https://www.framer.com/developers/components-reference#property-controls)
Property Controls allow users to pass props to a Code Component through the Framer interface. There is only one function needed for this feature, however the full type reference can be found in our [Property Controls Guide](https://www.framer.com/).
##### [`addPropertyControls(component, controls)`](https://www.framer.com/developers/components-reference#addpropertycontrols\(component-controls\))
```
import { addPropertyControls, ControlType } from "framer"

function Button(props) {
  const { tint = "#09F" } = props

  return button style={{ background: tint }}Hello</button
}

addPropertyControls(Button, {
  tint: {
    type: ControlType.Color
  }
})
```

## [Framer Motion](https://www.framer.com/developers/components-reference#framer-motion)
Also available in every Code Component is the entire [Motion](https://motion.dev/docs/framer) for React API. This can be imported from `"framer-motion"`.
```
import { animate, motion } from "framer-motion"
```

