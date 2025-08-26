# [Working with Components Instances](https://www.framer.com/developers/plugins-with-components#working-with-components-instances)
Plugins allow you to insert component instances in Framer. With the ability to insert instances with pre-configured properties you can utilize the full power of components in your Plugin. This enables you to build anything from component library UIs to full featured external integrations and more.
### [Inserting Component Instances](https://www.framer.com/developers/plugins-with-components#inserting-component-instances)
You can insert any component via its module URL. 
```
const instance = await framer.addComponentInstance({
  url: "https://framer.com/m/framer/Video.js"
})
```

This function expects an object with a required url. And an optional attributes you to customize the component. The second parameter is for attributes such as size, allowing you to insert the component with a specified size.
```
framer.addComponentInstance({
  url,
  attributes: { width: "900px", height: "600px" }
})
```

The properties of the component itself can be set via the controls attribute. In the case of a video component, this allows us to dynamically set the video url.
```
framer.addComponentInstance({
  url,
  attributes: {
    controls: {
      url: "https://path/to/video.mp4"
    }
  }
})
```

### [Inserting Detached Component Layers](https://www.framer.com/developers/plugins-with-components#inserting-detached-component-layers)
Components designed in Framer can be inserted as detached layers instead of a component instance. Similar to inserting component instances the attributes can be set.
```
const frame = await framer.addDetachedComponentLayers({
  url, 
  attributes: { title: user.name }
})
```

There is an optional layout flag to insert the layers as a layout section where Framer tries to match the component variants with the web page breakpoints.
```
framer.addDetachedComponentLayers({ url, layout: true })
```

### [Updating Control Values](https://www.framer.com/developers/plugins-with-components#updating-control-values)
Plugins are able to update the Control attributes on components, similar to updating style attributes. To do this well, you'll want to make sure the node you are trying to set the attributes of is a component.
```
if (!isCodeComponentNode(selection)) return

selection.setAttributes({
  controls: {
    radius: 10,
  }
})
```

To work with **Images** in Component controls, you can upload an image before you assign it to the control.
```
const image = await framer.uploadImage({
  image: "https://example.com/image.png",
  altText: "Alt Text"
})

selection.setAttributes({
  controls: {
    image,
  }
})
```

### [Module URLs](https://www.framer.com/developers/plugins-with-components#module-urls)
All components in Framer are portable and have unique URLs that can be used for sharing or insertion. In this case, you are able to use these URLs to insert components into a Framer project via a Plugin. We refer to these URLs as Module URLs.To copy a URL for one of your components, find your code component under the **Assets Panel** , then find your component Component and right click to **“Copy URL…”**. Now your clipboard will contain a url like so:
This URL points to the specific version of this component, and will forever point to that specific version. This is due to the string of characters after the `@` in the URL, known as a Save ID. To have the URL always point to the latest version of the Component, you can remove the `@` and everything after it, like so:
