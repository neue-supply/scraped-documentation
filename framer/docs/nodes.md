# [Working with Nodes](https://www.framer.com/developers/nodes#working-with-nodes)
Nodes are the building blocks that make up the content in a project. They are represented as "layers" in the editor UI. 
There are different types of nodes, each with their own set of properties and methods:
  * `FrameNode`
  * `TextNode`
  * `SVGNode`
  * `CodeComponentNode`
  * `UnknownNode`


### [Getting Nodes](https://www.framer.com/developers/nodes#getting-nodes)
Most of the time users will be selecting nodes on the canvas and running plugins based on their selection. The following code returns an array of nodes.
```
const selection = await framer.getSelection()
```

You can also subscribe to the selection to by notified when it changes.
```
function useSelection() {
  const [selection, setSelection] = useState<CanvasNode[]>([])

  useEffect(() => {
    return framer.subscribeToSelection(setSelection)
  }, [])

  return selection
}
```

All nodes have a unique ID. If you know the ID of a node, you can get it specifically.
```
const node = await framer.getNode("some-node-id")
```

It's possible to also get nodes all the Nodes in a Project that match a certain criteria. In these cases you can use the `getNodesWith…()` set of APIs.
This will return an array of Nodes that match the criteria you set, with options for Node types and attributes. 
```
// Get all frame nodes in a project.
const frameNodes = await framer.getNodesWithType("FrameNode")

// Get any kind of node that has a background color set.
const nodes = await framer.getNodesWithAttribute("backgroundColor")
```

This API can also be used to query within a selection. 
```
const selection = await framer.getSelection()
const selectedNode = selection.length === 1 ? selection[0] : null

// To get all nodes of a certain sub tree
if (selectedNode) {
  const frameNodes = await selectedNode.getNodesWithType("FrameNode")
  const nodes = await selectedNode.getNodesWithAttribute("backgroundColor")
  const nodes = await selectedNode.getNodesWithAttributeSet("backgroundColor")
}
```

A more complete use case, would be a hook that gets all the background images within set on Frames within a project. Here is an example implementation of that.
```
function useAllBackgroundImages() {
  const [images, setImages] = useState<ImageAsset[]>([])

  useEffect(() => {
    let active = true

    async function run() {
      // Get all Nodes with a background image set
      const nodes = await framer.getNodesWithAttributeSet("backgroundImage")

      // Use a Map to remove duplicates
      const uniqueImages = new Map<string, ImageAsset>()

      for (const item of nodes) {
        const image = item.backgroundImage
        if (!image) continue

        uniqueImages.set(image.id, image)
      }

      if (!active) return
      setImages(Array.from(uniqueImages.values()))
    }

    run()

    return () => {
      active = false
    }
  }, [])

  return images
}
```

### [Creating Nodes](https://www.framer.com/developers/nodes#creating-nodes)
Create a generic frame node. This creates a frame on the canvas
```
framer.createFrameNode()
```

To add text to the canvas
```
framer.addText()
```

Other more specific nodes can be used to add text, images or code components. See docs on how to create them:
  * [Code Components](https://www.framer.com/)
  * [Images and SVGs](https://www.framer.com/)


### [Traits](https://www.framer.com/developers/nodes#traits)
Traits are a way to differentiate between kinds of nodes, or nodes with specific attributes.
For example, to check if the selected node is text, we can use the `isTextNode` trait function:
```
const selection = await framer.getSelection()

for (const node of selection) {
  // We need to check what the node is because 
  // the `setText` method is only available on 
  // text nodes.
  if (isTextNode(node)) {
    node.setText("Hello!")
  }
}
```

Other trait functions for checking the node type include:
  * `isFrameNode`
  * `isTextNode`
  * `isSVGNode`
  * `isCodeComponentNode`


Traits can also be used to check if a node has a specific attribute. This is useful because different node types may have similar attributes. For example, all nodes have a position.
To check if a node has a specific attribute, use a trait function that begins with the word "supports".
For example, logging out all the locked layers that support setting a background image:
```
const selection = await framer.getSelection()

for (const node of selection) {
  if (supportsBackroundImage(node) {
    console.log(node)
  }
}
```

Some other trait functions for checking node attributes include:
  * `supportsPosition`
  * `supportsVisible`
  * `supportsRotation`
  * `supportsBackgroundGradient`
  * `supportsBorderRadius`


To see a full list, check the types file `index.d.ts`.
### [Replicas](https://www.framer.com/developers/nodes#replicas)
Every node has a `isReplica` property that indicate if the node is a replica. Replica nodes are used within non-primary Breakpoints and Component variants and inherit attributes from the primary variant or breakpoint. Once a specific attribute is overridden on a replica node, it is no longer inherited from the primary node and is instead set on that replica.
### [Children & Parents](https://www.framer.com/developers/nodes#children-parents)
If you need to access the children or parents of a layer, you can do that via the `getParent()` or `getChildren()` async functions.
### [Working with Async Layer APIs](https://www.framer.com/developers/nodes#working-with-async-layer-apis)
Example of combining async APIs for layers.
```
useEffect(() => {
  let active = true;
  
  async function run() {
    if (!active) return;
    
    const parentNode = selection[0];

    if (!parentNode || selection.length !== 1) {
      setState(null);
      return;
    }
  
    const layerPromises = [parentNode.getChildren(), parentNode.getRect()]
    const [children, parentRect] = await Promise.all(layerPromises)
  
    // Exit to not support no selection or multiselect
    if (children.length !== 1 || !parentRect) {
      setState(null);
      return;
    }
  
    const singleChild = children[0];
    const childRect = await singleChild.getRect()
    
    if (!childRect) {
      setState(null);
      return;
    }
  
    setState({
      parent: parentNode,
      child: singleChild,
      parentRect,
      childRect,
    });
  }

  run()
  
  // cleanup function
  return () => {
    active = false;
  };
}, selection)
```

