# [Drag & Drop](https://www.framer.com/developers/drag-and-drop#drag-drop)
You can make images, SVG, and component instances, and detached component layers draggable using the `framer.makeDraggable()` API. The function requires an HTML element as its first argument, and a function to generate the drag data as its second argument.
```
const cleanup = framer.makeDraggable(div, () => {
  return {
    type: "image",
    image: "https://www.example.com/image.jpg",
    
    // Optional, used while dragging
    // Make sure to use a small image so it loads fast
    previewImage: "https://www.example.com/image.jpg",
  }
})
```

Make sure to call the returned cleanup function when you are no longer rendering the element.
## [Supported drag types](https://www.framer.com/developers/drag-and-drop#supported-drag-types)
The following data types can be inserted via dragging.
  * `image`
  * `svg`
  * `componentInstance`
  * `detachedComponentLayers`


## [Draggable](https://www.framer.com/developers/drag-and-drop#draggable)
If you are building in React we offer a `Draggable` component that makes this API simpler to work with. The component needs to be wrapped around the draggable element which can be any HTML element. It has a single `data` property. You can also pass in a function to only generate the data when requested. Make sure to only render a single element as the child. And if you want to conditionally render the draggable you have to add the condition around the outer draggable component.
```
const framerIcon = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path d="M5 2.5h10v5h-5Zm0 5h5l5 5H5Zm5 5v5l-5-5Z"/></svg>`

function MyDraggableSVG() {  
  const handleClick = () => {
    void framer.addSVG({ svg: framerIcon })
  }
  
  return (
    Draggable data={{
      type: "svg",
      svg: framerIcon,
      invertInDarkMode: true // if enabled the svg drag preview will be inverted in dark mode
    }}
      button onClick={handleClick}
        svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"
          path d="M5 2.5h10v5h-5Zm0 5h5l5 5H5Zm5 5v5l-5-5Z"/>
        </svg
      </button
    </Draggable
  )
}
```

## [Inserting Components](https://www.framer.com/developers/drag-and-drop#inserting-components)
You can insert components as either instances or detached layers. A component can only be inserted as detached layers when it has been created visually in Framer.
```
Draggable
    data={{
        type: "detachedComponentLayers",
        url: "https://framer.dev/m/Hero.js@lI6PA86v8ICaqYVTRP1H",
        layout: true, // if enabled the layers will be inserted as a layout block
    }}

    button
        onClick={() => {
            void framer.addDetachedComponentLayers({
                url: "https://framer.dev/m/Hero.js@lI6PA86v8ICaqYVTRP1H",
                layout: true,
            })
        }}
    
        Layout Block
    </button
</Draggable
```

