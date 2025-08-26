[Reference](https://www.framer.com/developers/reference)
[Drag & Drop](https://www.framer.com/developers/reference/plugins-drag-and-drop)
makeDraggable
# makeDraggable
### makeDraggable
Allow any HTML element to become draggable.
```
framer.makeDraggable(
  element,
  () => {
    return {
      type: "image",
      image: "https://www.example.com/image.jpg",
      previewImage: "https://www.example.com/image.jpg",
    };
  },
  (result) => {
    if (result.status === "error") {
      framer.notify(result.reason ?? "An error happened");
      return;
    }

    framer.notify("Image uploaded successfully");
  }
);


```

### [Parameters](https://www.framer.com/developers/reference/plugins-make-draggable#parameters)
  * `element` – The element to make draggable.
  * `getDragData` – The [DragData](https://www.framer.com/developers/reference/plugins-drag-and-drop) to be inserted.
  * `onDragComplete` – A callback function triggered when the drag finishes.


### [Returns](https://www.framer.com/developers/reference/plugins-make-draggable#returns)
  * `Promise<void>` – Cleanup function remove the draggable behavior from the element and to stop all of the added listeners.


