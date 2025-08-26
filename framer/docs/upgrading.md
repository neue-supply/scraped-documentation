# [Upgrading Plugins](https://www.framer.com/developers/upgrading#upgrading-plugins)
During the Plugin Beta we are iterating quickly on the APIs based on new features and feedback. Sometimes this leads to breaking API changes, meaning you Plugin code has to be updated in order to continue working. This page will help you upgrade your Plugin to the latest APIs.
## [Default Mode Deprecation](https://www.framer.com/developers/upgrading#default-mode-deprecation)
The _default_ mode has been renamed to _canvas_. Framer still allows opening older plugins in default mode, but in a couple of weeks these plugins won't even open anymore. To start using the new _canvas_ mode, follow the next few steps:
  1. Upgrade the plugin library to the latest version
  2. Open the `framer.json` file and change the _default_ mode to _canvas_ (if you support that mode)
  3. If you have conditional logic in your Javascript code that checks for the _default_ mode you'll want to change this to _canvas_ as well.


## [Breaking Version #4](https://www.framer.com/developers/upgrading#breaking-version-4)
#### [Assignable Color Styles](https://www.framer.com/developers/upgrading#assignable-color-styles)
Color Styles can now be assigned to color related attributes. Before this change, only color string could be used e.g `"rgba(242, 59, 57, 1)"`.
This is only a breaking change if your plugin reads and makes use of these attributes. Setting color attributes is not affected and will still work as normal.
To handle the new Color Style type, check for it when working the an attribute's value.
```
if (isColorStyle(frameNode.color)) {
  console.log("Frame color is:", frameNode.color.light)
} else {
  console.log("Frame color is:", frameNode.color)
}
```

## [Breaking Version #3](https://www.framer.com/developers/upgrading#breaking-version-3)
#### [Collection changes](https://www.framer.com/developers/upgrading#collection-changes)
It's now possible to interact with any kind of collection in the CMS, even if it's not controlled by the plugin. To allow this, we make a distinction between a collection that's fully controlled by a plugin and a collection of any kind. 
These are called `ManagedCollection` and `Collection` respectively. 
Update your plugin by doing the following:
  * In `framer.json`, rename `configureCollection` to `configureManagedCollection` and `syncCollection` to `syncManagedCollection`
  * Rename `framer.getCollection()` to `framer.getManagedCollection()`
  * Rename any existing references to `Collection` to `ManagedCollection`
  * Add a title field to the collection using `setFields`
  * When adding item data using `addItems`, move the `title` attribute into `fieldData`


```
managedCollection.setFields([
  //...
  { id: "title", type: "string", name: "Title" }
  //...
])

managedCollection.addItems([
  //...
  {
    id: "example-item-1",
    slug: "example-item-1",
    fieldData: {
      title: "Example Item 1"
    }
  }
  //...
])
```

See our updated [CMS guide](https://www.framer.com/#managed-collections) for more info.
## [Breaking Version #2](https://www.framer.com/developers/upgrading#breaking-version-2)
### [Node renames](https://www.framer.com/developers/upgrading#node-renames)
To prevent confusion we are renaming the `CodeComponentNode` to `ComponentInstanceNode`. And the `SmartComponentNode` is now named `ComponentNode`. The term smart is more of a marketing name so we are removing it from the public API.
### [Adding component instances](https://www.framer.com/developers/upgrading#adding-component-instances)
Similar to the node rename the component insert and component drag type have been renamed to component instance.
```
Draggable data={{ type: "componentInstance", url: "https://framer.dev/m/Tomato-v4Ik.js" }}
  button onClick={() => {
    void framer.addComponentInstance({ url: "https://framer.dev/m/Tomato-v4Ik.js" })
  }} />
</Draggable
```

### [Attribute rename](https://www.framer.com/developers/upgrading#attribute-rename)
Components instances used to have the `controlAttributes` attribute that contains all control values. We are renaming this to just be `controls`.
```
const selection = await framer.getSelection()
const [singleNode] = selection
if (selection.length === 1 && isComponentInstance(singleNode)) {
  const controls = singleNode.controls
  const image = controls.avatar
  if (isImageAsset(image)) {
    console.log("URL" + image.url)
  }
}
```

## [Breaking Changes #1](https://www.framer.com/developers/upgrading#breaking-changes-1)
### [framer.json File](https://www.framer.com/developers/upgrading#framer-json-file)
Older Plugins may not have a `framer.json` file which is now required, you can create one on one the [generator page](https://www.framer.com/).
