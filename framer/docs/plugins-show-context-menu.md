[Reference](https://www.framer.com/developers/reference)
showContextMenu
# showContextMenu
### showContextMenu
Show a context menu at a given location.
```
await framer.showContextMenu(
  [
    {
      label: "Edit",
      enabled: item.isEditable,
      onAction: () => editItem(item)
    },
    {
      label: "Status",
      submenu: [
        {
          label: "Pending",
          checked: priority === "pending",
          onAction: () => setStatus("pending"),
        },
        {
          label: "Done",
          checked: priority === "done",
          onAction: () => setStatus("done"),
        },
      ],
    },
    { type: "separator" },
    {
      label: "Remove",
      onAction: () => removeItem(item),
    },
  ],
  {
    location: { x: event.clientX, y: event.clientY },
    placement: "bottom-left",
    width: 220,
  }
)


```

### [Parameters](https://www.framer.com/developers/reference/plugins-show-context-menu#parameters)
  * `menuItems: MenuItem[]` — The entries to add to the context menu.
  * `config: ContextMenuConfig` — Configuration for showing the context menu.


```
interface ContextMenuConfig {
    /**
     * Coordinates of the anchor point.
     */
    location: { x: number; y: number }
    /**
     * Placement of the menu relative to the anchor point.
     */
    placement?: "top" | "bottom" | "left" | "right" | "top-left" | "top-right" | "bottom-left" | "bottom-right"
    /**
     * Sets fixed width for the menu. If not set, the menu width is based on the content.
     */
    width?: number
}
```

### [Returns](https://www.framer.com/developers/reference/plugins-show-context-menu#returns)
  * `Promise<void>`


### [Caveats](https://www.framer.com/developers/reference/plugins-show-context-menu#caveats)
  * `placement` is relative to the `location`.


