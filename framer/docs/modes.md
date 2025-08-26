# [Plugin Modes](https://www.framer.com/developers/modes#plugin-modes)
The concept of modes has been introduced to make Plugins context aware. When your plugin supports a contextual mode, it will become available as a launch option within that specific context, for example in the image picker or CMS.
The plugin mode is available when your plugin launches and never changes while your plugin is active. The _Open Development Plugin…_ action is shown in all places where you can contextually launch your plugin in a mode.
Plugins can only launch in the modes that are defined within their `framer.json`. Read more on how to set this up on the [configuration page](https://www.framer.com/developers/configuration).
## [Available modes](https://www.framer.com/developers/modes#available-modes)
  * `code` — Expected to edit the currently open code file
  * `image` — Expected to provide an image
  * `canvas` — Launched from the canvas
  * `editImage` — Expected to edit the currently selected image
  * `collection`
  * `configureManagedCollection` — Expected to configure the active collection
  * `syncManagedCollection` — Expected to synchronize the active collection


## [Image Modes](https://www.framer.com/developers/modes#image-modes)
Plugins that work on images are recommended to support one or both of the available image Modes. When your plugin supports this, an option to launch your plugin will be displayed in the image picker. And it will work anywhere where we show the image picker. On the canvas, in the CMS, and in the Localization table.
The image modes provide high level APIs to update images so you don't need to write logic to support specific nodes. And it also means that nodes that support multiple images (e.g. code components) just work like you'd expect without having to write complex logic.
#### [Image Mode](https://www.framer.com/developers/modes#image-mode)
Your plugin is expected to allow the user to pick an image they want to use. The Unsplash plugin uses this mode. The selected image is send to Framer via `framer.setImage`. That's also the only method you are allowed to use in this mode.
#### [Edit Image Mode](https://www.framer.com/developers/modes#edit-image-mode)
Plugins that support `editImage` mode are only available if the user already has an image set. This image can be requested via the `framer.getImage()` method. This mode is great for plugins that want to make edits to an existing image (e.g. Photoshop). Just like with image mode, the plugin can update the image via `framer.setImage`.
## [Reading current mode](https://www.framer.com/developers/modes#reading-current-mode)
When a plugins is launched in a specific mode it has access to a limited subset of API methods. You can check the mode in which your plugin runs and branch off your code based on that.
```
if (framer.mode === "image" || framer.mode === "editImage") {
  // Do image mode specific logic
  return
}

if (framer.mode === "canvas") {
  // Plugin runs in canvas mode - access to all APIs.
  return
}
```

### [Unsupported Mode](https://www.framer.com/developers/modes#unsupported-mode)
This error can happen when you attempt to launch a plugin in a specific mode from a certain context. For example when you attempt to load a plugin from a URL in the Image Picker. In this case your plugin should support either the `image` or `editImage` mode and declare it in the [Plugin Manifest](https://www.framer.com/developers/configuration).
