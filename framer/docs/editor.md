# [Working with the Editor UI](https://www.framer.com/developers/editor#working-with-the-editor-ui)
Plugins can programmatically control the Framer interface, making them feel more integrated into the UI.
### [Going to a Node](https://www.framer.com/developers/editor#going-to-a-node)
You can automatically adjust the viewport's pan and zoom so that a node appears in the center. This is the equivalent to using **Zoom to Selection** in the UI, except you can use any list of Nodes.
```
// Scroll and zoom the viewport to show a specific node.
await framer.zoomIntoView("node-id")

// Scroll and zoom to fit multiple nodes into the viewport.
await framer.zoomIntoView(["node-id-1", "node-id-2"])
```

If you already have a reference to a node, you can call `zoomIntoView` directly on it.
```
await node.zoomIntoView()
```

