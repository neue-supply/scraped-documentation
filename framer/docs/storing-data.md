# [Storing Data](https://www.framer.com/developers/storing-data#storing-data)
As a Plugin author you may want to store some data that your Plugin can use the next time it opens. There are three options for storing data:
  1. Storing global data on a project level
  2. Storing data on a specific node
  3. Storing user specific data on the client 


> **Important:** Don’t use this API to store sensitive data such as secret keys or access tokens.
## [Storing global project data](https://www.framer.com/developers/storing-data#storing-global-project-data)
You may want to store data at the project level that is shared between users. There are API methods available on the `framer` export for this.
```
// Set global data on the project.
await framer.setPluginData('key', 'value');

// Get global data from the project.
const data = await framer.getPluginData('key');
```

**Note:** A data entry only supports strings and can contain a maximum of `2kB` `4kB`. If you exceed this limit, the `setPluginData` method will throw. It is still possible to delete plugin data.
## [Storing data on a node](https://www.framer.com/developers/storing-data#storing-data-on-a-node)
If your Plugin works on the canvas, you may want to store some data on a specific node. For example, a flag to indicate that your Plugin previously interacted with this Node, or some other metadata to render UI.
Every Node supports the same storage API methods for storing plugin data. The [Collection](https://www.framer.com/) instance also supports these methods.
```
const node = await framer.getNode('nodeId')

// Set data on a node.
await node.setPluginData('key', 'value');

// Get data from a node.
const data = await node.getPluginData('key');

// Get all data key from a node.
const keys = await node.getPluginDataKeys()
```

> **Note:** A data entry only supports strings and can contain a maximum of `2kB` `4kB` per Node. If you exceed this limit, the `setPluginData` method will throw. It is still possible to delete plugin data.
## [Removing data](https://www.framer.com/developers/storing-data#removing-data)
Both project and node data can be deleted by setting the data value to `null`. This will automatically remove the key.
```
// Remove data from the project.
await framer.setPluginData('key', null);

// Remove data from a node.
const node = await framer.getNode('nodeId')
await node.setPluginData('key', null);

// Remove all global project data. The same technique 
// can also be used for nodes.
const keys = await framer.getPluginDataKeys()

for (const key of keys) {
  await framer.setPluginData(key, null);
}
```

## [Storing user specific data on the Client](https://www.framer.com/developers/storing-data#storing-user-specific-data-on-the-client)
Some things, such as user preferences or authentication tokens should not be stored on the project but be specific to each user. For these things you can use the built-in and APIs. Plugins run in a sandboxed iframe on a unique origin and will not be able to read each others data when you use these storage APIs
