[Reference](https://www.framer.com/developers/reference)
[Drag & Drop](https://www.framer.com/developers/reference/plugins-drag-and-drop)
Draggable
# Draggable
A React component that makes it's child draggable.
```
Draggable
  data={{
    type: "image",
    image: "https://www.example.com/image.jpg",
    previewImage: "https://www.example.com/image.jpg",
  }}
  onDragComplete={(result) => {
    if (result.status === "error") {
      framer.notify(result.reason ?? "Unknown error");
      return;
    }

    framer.notify("Image uploaded successfully");
  }}

  Image src="https://www.example.com/image.jpg" />
</Draggable
```

### [Parameters](https://www.framer.com/developers/reference/plugins-drag-and-drop-draggable#parameters)
  * `data` – The [DragData](https://www.framer.com/developers/reference/plugins-drag-and-drop) or a function to generate the data to be inserted.
  * `onDragComplete` – A callback function triggered when the drag finishes.


### [Caveats](https://www.framer.com/developers/reference/plugins-drag-and-drop-draggable#caveats)
  * Make sure to only render a single element as the child.
  * If you want to conditionally render the draggable you have to add the condition around the outer draggable component.


