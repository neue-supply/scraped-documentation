[Reference](https://www.framer.com/developers/reference)
showUI
# showUI
### showUI
Show the plugin window.
```
framer.showUI({
  position: "center",
  height: 300,
  width: 220
})
```

### [Parameters](https://www.framer.com/developers/reference/plugins-show-ui#parameters)
  * `options?: UIOptions` — The options for how to show the UI.
    * `width?: number` — The initial UI width.
    * `height?: number` — The initial UI height.
    * `position?: "center" | "top left" | "bottom left" | "top right" | "bottom right"` — The initial window position, defaults to top left.
    * `resizable?: true | false | "width" | "height"` — Whether the UI is resizable.
    * `minWidth?: number` — Minimum UI width.
    * `minHeight?: number` — Minimum UI height.
    * `maxWidth?: number` — Maximum UI width.
    * `maxHeight?: number` — Maximum UI height.


### [Returns](https://www.framer.com/developers/reference/plugins-show-ui#returns)
  * `Promise<void>`


