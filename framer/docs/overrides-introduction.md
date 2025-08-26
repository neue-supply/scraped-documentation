# [What are Code Overrides?](https://www.framer.com/developers/overrides-introduction#what-are-code-overrides)
Code Overrides are small functions that you can use to modify the properties or functionality of any layer in Framer. They are applied to the layer on the canvas, however they are only active in the preview and on your published site.
Please note,**overrides must use React 18 compatible code**. This includes using `forwardRef` to ensure effects and links keep working when overriding the associated layer.
### [You might not need Code Overrides](https://www.framer.com/developers/overrides-introduction#you-might-not-need-code-overrides)
Overrides give you control over the rendering of any Layer in Framer, which in turn means it can be easy to unintentionally break the built-in functionality of Framer. Recently, many of the common use cases for Overrides have been replaced by first class features which are optimized by default and less likely to break things.
  * Animating Text & Layers → [**Effects**](https://www.framer.com/academy/topics/effects)
  * User Interactions → [**Components**](https://www.framer.com/academy/lessons/components)
  * Using Dynamic Data → [**Fetch**](https://www.framer.com/academy/lessons/fetch)


### [Getting Started](https://www.framer.com/developers/overrides-introduction#getting-started)
You can create Code Overrides directly inside Framer. Go to the properties panel and create a new file under the Code Overrides section. This will create an Examples file by default where you can see examples of common Code Overrides.
### [A Basic Override](https://www.framer.com/developers/overrides-introduction#a-basic-override)
The is the basic code for any Override, which is essentially a normal [React Higher Order Component](https://legacy.reactjs.org/docs/higher-order-components.html). The example below modifies the `opacity` property of the element it is applied to. Framer uses TypeScript types to detect your overrides, hence the `ComponentType`. It is important to always apply the existing props, otherwise you may break the appearance or functionality of your Layer.
```
import { forwardRef, type ComponentType } from "react"

export const withLowerOpacity = (Component): ComponentType => {
  // This part of the code is only run once when creating the component
  // You usually do not need anything here.
  
  return forwardRef((props, ref) => {
    // This part runs every time the component is rendered.
    return Component ref={ref} {...props} style={{ ...props?.style, opacity: 0.5 }} />
  })
}
```

Now that you have your new Override, you can apply it to any element on the canvas from the same section in the property panel. If you now preview or publish your site, the element will have an opacity of 0.5.
