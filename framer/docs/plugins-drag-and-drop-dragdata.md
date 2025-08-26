[Reference](https://www.framer.com/developers/reference)
[Drag & Drop](https://www.framer.com/developers/reference/plugins-drag-and-drop)
DragData
# DragData
An object that represents the data to be dragged.
##### [Supported drag types](https://www.framer.com/developers/reference/plugins-drag-and-drop-dragdata#supported-drag-types)
The following data types can be inserted via dragging.
```
{
    type: "image;
    name: string;
    image: string;
    previewImage?: string;
    altText?: string;
    resolution?: "auto" | "lossless" | "small" | "medium" | "large" | "full",
}
```

```
{
    type: "svg";
    name: string;
    svg: string;
    previewImage?: string;
    /** Inverts SVG drag preview in dark mode. Defaults to true. */
    invertInDarkMode?: boolean;
}
```

###### [Component Instance](https://www.framer.com/developers/reference/plugins-drag-and-drop-dragdata#component-instance)
```
{
    type: "componentInstance";
    name: string;
    url: string;
    previewImage?: string;
    /** Should it be inserted as a Stack or a Frame. **/
    attributes?: Partial<EditableComponentInstanceNodeAttributes>;
}
```

###### [Detached Component Layers](https://www.framer.com/developers/reference/plugins-drag-and-drop-dragdata#detached-component-layers)
A component can only be inserted as detached layers when it has been created visually in Framer.
```
{
    type: "detachedComponentLayers";
    name: string;
    url: string;
    previewImage?: string;
    /** If enabled the layers will be inserted as a layout block. **/
    layout?: boolean;
    attributes?: Partial<EditableComponentInstanceNodeAttributes>;
}
```

