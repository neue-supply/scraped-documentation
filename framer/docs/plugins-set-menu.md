[Reference](https://www.framer.com/developers/reference)
setMenu
# setMenu
### setMenu
Register a global plugin menu.
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

### [Parameters](https://www.framer.com/developers/reference/plugins-set-menu#parameters)
  * `items: MenuItem[]` — The entries to add to the menu.


### [Returns](https://www.framer.com/developers/reference/plugins-set-menu#returns)
  * `Promise<void>`


