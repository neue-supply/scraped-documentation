[Reference](https://www.framer.com/developers/reference)
closePlugin
# closePlugin
Close and terminate the plugin.
```
await framer.closePlugin("Synchronization successful", {
    variant: "success",
})
```

### [Parameters](https://www.framer.com/developers/reference/plugins-close-plugin#parameters)
  * `message?: string` — An optional message to show in the toast that will be shown.
  * `options?: ClosePluginOptions`
    * `variant?: NotificationVariant` — What variant of toast to show.


### [Returns](https://www.framer.com/developers/reference/plugins-close-plugin#returns)
  * `Promise<void>`


