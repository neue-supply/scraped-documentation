# [Building a Plugin Interface](https://www.framer.com/developers/interface#building-a-plugin-interface)
Plugins give you full control over the styling, allowing you to create any interface you’d like. The plugin template includes a minimal set of styles, consisting of global styles to help your plugin fit into the Framer UI.
### [Creating UI](https://www.framer.com/developers/interface#creating-ui)
With the Plugin template many semantic HTML are styled for you already. For example a structure like the following will fit in naturally into the Framer interface by default.
```
main
  hr />
  
  input type="number" />
  buttonAdd Layer</button
</main
```

We do not maintain an official set of reusable components, however for a more in-depth library from the community, you can try [Framer Toolbox](https://github.com/triozer/framer-toolbox) from [Cédric](https://github.com/triozer). This library includes tools and Components for elements like Segmented Controls.
### [Showing UI](https://www.framer.com/developers/interface#showing-ui)
By default the UI isn't shown and only a toast appears while your plugin is running. To make the UI appear you can call `framer.showUI`. That method comes with an optional UI configuration.
```
framer.showUI({
  position: "top left", // Optional, Allowed: "top left", "center", etc.
  width: 240, // Optional
  height: 245, // Optional
  resizable: true, // Optional (default false). Allowed: true, false, "width", "height"
  minWidth: 100, // Optional
  minHeight: 100, // Optional
  maxWidth: 300, // Optional (default Infinity)
  maxHeight: 300, // Optional (default Infinity)
})
```

You can hide the UI again with the following method.
```
framer.hideUI()

// It's possible to conditionally display a UI
if (needsLogin) {
  framer.showUI()
} else {
  framer.hideUI()
}
```

To stop the plugin programmatically you can call `framer.closePlugin`. That method comes with an optional message.
```
framer.closePlugin("Image flipped successfuly", {
  variant: "success" // Optional, other options are "info" and "error"
})
```

### [Building UI](https://www.framer.com/developers/interface#building-ui)
With the Plugin template many semantic HTML are styled for you already. For example a structure like the following will fit in naturally into the Framer interface by default.
```
main
  hr />
  
  buttonAdd Layer</button
</main
```

### [Color Tokens](https://www.framer.com/developers/interface#color-tokens)
Framer provides a selection of CSS color variables that automatically adjust based on the light / dark mode of Framer. 
`--framer-color-tint`
`--framer-color-tint-dimmed`
`--framer-color-tint-dark`
`--framer-color-bg`
`--framer-color-bg-secondary`
`--framer-color-bg-tertiary`
`--framer-color-divider`
`--framer-color-text`
`--framer-color-text-reversed`
`--framer-color-text-secondary`
`--framer-color-text-tertiary`
### [Dark / Light Mode](https://www.framer.com/developers/interface#dark-light-mode)
If you need to adjust more UI based on the current theme, you can use CSS rules that only apply when a specific theme is active.
```
/* Only apply in dark mode */
[data-framer-theme="dark"] .my-element {
  color: #fff;
}

/* Only apply in light mode */
[data-framer-theme="light"] .my-element {
  color: #000;
}
```

If you need to access the current theme from within your app, you can access it with the following code.
```
// Will return “light” or “dark”
document.body.dataset.framerTheme
```

### [Built-in Classes](https://www.framer.com/developers/interface#built-in-classes)
Currently the plugin template includes a couple CSS classes for common UI in Framer.
  * `framer-button-primary` applied to a `<button />` element to make it a primary button color.
  * `framer-divider` applied to a `<div />` to be a horizontal rule.


### [Displaying Notifications](https://www.framer.com/developers/interface#displaying-notifications)
Your Plugin can display notifications displayed to users via `framer.notify`
```
const notification = framer.notify("An action was completed", {
    button: { text: "Undo", onClick: handleUndo },
    durationMs: 3000,
    onDisappear: handleDisappear,
    variant: "info", // Or 'success', 'warning', 'error'
})

// In case you want to close the notification programatically.
notification.close()


```

### [Displaying Menus](https://www.framer.com/developers/interface#displaying-menus)
Plugins can utilize two type of menus:
  * **Header Menu** : menu always anchored to the plugin name in the top header of the plugin
  * **Context Menu** : can be shown anywhere in the plugin interface


To display a menu in the plugin header, use 
```
await framer.setMenu([
    {
        label: "New",
        onAction: newFile,
    },
    {
        type: "separator",
    },
    {
        label: "Log Out",
        onAction: logOut,
    },
])
```

To display a menu at any location in your plugin interface, use `framer.showContextMenu[](https://www.framer.com/developers/reference/plugins-show-context-menu)`
```
await framer.showContextMenu(
  [
    {
      label: "Edit",
      enabled: item.isEditable,
      onAction: () => editItem(item)
    },
    {
      label: "Remove",
      onAction: () => removeItem(item),
    },
  ],
  {
    location: { x: event.clientX, y: event.clientY },
  }
)
```

