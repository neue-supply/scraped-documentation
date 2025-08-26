[Reference](https://www.framer.com/developers/reference)
[Drag & Drop](https://www.framer.com/developers/reference/plugins-drag-and-drop)
onDragComplete
# onDragComplete
### onDragComplete
A callback triggered when a drag finishes.
```
onDragComplete={(result) => {
  if (result.status === "error") {
    framer.notify(result.reason ?? "Unknown error");
    return;
  }

  framer.notify("Image uploaded successfully");
}}
```

### [Parameters](https://www.framer.com/developers/reference/plugins-drag-and-drop-on-drag-complete#parameters)
  * `status: "success" | "error"` – Whether the drag was successful or not.
  * `nodeId` – The ID of the node that was inserted. This field is only available if drag succeeded.
  * `reason` – The reason why the drag failed. This field is only available if the drag failed.


