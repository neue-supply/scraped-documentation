# [Plugin Concepts](https://www.framer.com/developers/concepts#plugin-concepts)
Helpful concepts to help you become successful when creating Plugins.
## [Plugin Architecture](https://www.framer.com/developers/concepts#plugin-architecture)
A plugin is a small website that runs inside of Framer in a secure iframe and interacts with the Framer editor via the API. In the case of the plugin template, it is a React application with everything ready to go.
Plugins will run in floating window by default, but can also work without any UI at all. This is set up in the `main.tsx` file, where `framer.showUI` is called. This triggers the opening of your plugin and defines the initial location and position of the window.
```
framer.showUI({ position: "top left", width: 240, height: 245 })
```

The main interface of the plugin template lives in the `App.tsx` file. Try making a change in the file to see it update in Framer. Simple plugins can likely fit most of their logic within this file.
```
export function Example() {
  const selection = useSelection()

  const handleAddSvg = async () => {
    await framer.addSVG({
      svg: `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path d="M5 2.5h10v5h-5Zm0 5h5l5 5H5Zm5 5v5l-5-5Z"/></svg>`,
      name: "framer.svg",
    })
  }

  return (
    main
      div className="frame-info"
        p{JSON.stringify(selection, null, 2)}</p
      </div
      button onClick={handleAddSvg}Add SVG</button
    </main
  )
}
```

The plugin template has Framer styling built-in to many common elements. These styles live in the `globals.css` file, however you shouldn’t need to edit them directly. Custom styling of your plugin can be done in the `App.css` file. Learn more in the [styling guide](https://www.framer.com/developers/interface).
## [Plugin Run Model](https://www.framer.com/developers/concepts#plugin-run-model)
Most of the time plugins are recognized as floating windows in Framer. They can however also run without any UI at all. In these cases a toast will appear while the plugin is running. This is useful for action based plugins that may not need any additional configuration.
## [Code Concepts](https://www.framer.com/developers/concepts#code-concepts)
To effectively write code for the plugin, you'll have to understand two fairly advanced JavaScript concepts: async and traits.
Framer projects are tree like structures that have a project as the root containing pages, which then contain different types of nodes like a Frame, Graphic or Component. Because your plugin runs in an isolated space, it has to request and download project data using the API. Because the project data typically is really big, it can only do so in pieces and that's where async comes in. Any time you request a piece of project data you'll have to wait for the response using `await`:
```
const rect = await node.getRect()

console.log(rect.width)
```

### [Traits](https://www.framer.com/developers/concepts#traits)
When you have a piece of project data, you typically don't know what it is. For example, you know that the project contains pages, but you don't know what nodes are on a page because they can be Frames, Graphics, etc. You can ask a node directly what it is which works well, but it's often easier to ask a node if it "supports" something or not. For example, different types of nodes all "support" setting a border radius or background color. We call these traits and they're really handy if you want to for example see if the current selection supports setting a background color, independent of the type of node that it is:
```
import { supportsRotation } from "framer-plugin"

if (supportsRotation(node)) {
  console.log(node.rotation) // Will not error
}
```

