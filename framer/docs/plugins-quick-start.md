# [Quick Start](https://www.framer.com/developers/plugins-quick-start#quick-start)
This guide will help you get up and running with a Framer Plugin. 
## [Installation](https://www.framer.com/developers/plugins-quick-start#installation)
To get started with Plugins, you can run `npm create framer-plugin@latest` in your terminal. This will walk you through a few steps and will create a new Plugin folder with a basic Plugin setup. If you prefer something other than npm, all major package managers are supported. 
If you’d looking to build a CMS Plugin specifically, we recommend starting with the CMS Starter Plugin. Learn how to get started with it in the [CMS guide](https://www.framer.com/developers/cms).
```
// npm (recommended)
npm create framer-plugin@latest

// pnpm 
pnpm create framer-plugin

// yarn
yarn create framer-plugin
```

> ###### [Manual Installation](https://www.framer.com/developers/plugins-quick-start#manual-installation)
> If you have an existing project you’d like to use the Plugin API from, you can install the `framer-plugin` package directly. However, we currently do not officially support this.
## [Running your Plugin](https://www.framer.com/developers/plugins-quick-start#running-your-plugin)
After the initial setup, navigate into your Plugin folder using `cd your-plugin` and then run `npm run dev`. This command is what you’ll need to run at each time you want to develop your Plugin. With this dev command running, your Plugin can be picked up by Framer and will automatically update when you change any files from within your Plugin folder.
> ###### [Node Version too low?](https://www.framer.com/developers/plugins-quick-start#node-version-too-low)
> Framer uses the latest libraries that require a modern version of node. We recommend upgrading node or using a node version manager like `n` if you swap versions often.
## [Opening in Framer](https://www.framer.com/developers/plugins-quick-start#opening-in-framer)
Now you have a Plugin running on your computer the next step is opening it within Framer. You'll need to enable the Developer Tools preference from within the Plugin section in the main menu. 
Once Developer Tools are enabled, open the Plugin menu from the toolbar, and click “Open Development Plugin”. This will run your Plugin.
> ###### [Ad-blockers](https://www.framer.com/developers/plugins-quick-start#ad-blockers)
> Some Ad-blockers or browsers like Brave try to restrict access to localhost. If you have issues running your development Plugin, allow-listing framer.com may help.
Now that your Plugin up and running, you can add some functionality to your app. Some ways to start would be to try manipulating [Nodes](https://www.framer.com/developers/nodes), inserting [Components](https://www.framer.com/developers/plugins-with-components), syncing to the [CMS](https://www.framer.com/developers/cms), or to start [styling your plugin](https://www.framer.com/developers/interface).
