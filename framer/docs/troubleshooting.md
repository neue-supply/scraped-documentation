# [Troubleshooting](https://www.framer.com/developers/troubleshooting#troubleshooting)
Fixes to common problems you may run into. If you run into anything that isn't covered here, please let us know.
### [Failed to load Development Plugin](https://www.framer.com/developers/troubleshooting#failed-to-load-development-plugin)
This message displays when your Development Plugin fails to load. Here are a few steps to troubleshoot:
  * Ensure your plugin development server is running. See the [QuickStart guide](https://www.framer.com/) for instructions how to run the Plugin
  * Check if another process is using the expected port of your Plugin Development server


### [Plugin Framer.json is missing](https://www.framer.com/developers/troubleshooting#plugin-framer-json-is-missing)
Plugins require a `framer.json` file that defines the configuration of the plugin. Some plugins created at an earlier stage of the beta may not have this setup correctly yet. You can follow the following steps.
  1. Create a `framer.json` file in the root of your plugin directory. See the [generator](https://www.framer.com/) page to create one.
  2. Upgrade the dependencies of your plugin in `package.json`. It is recommended to update all dependencies but ensure you have the latest version of `vite-plugin-framer` by running `npm install vite-plugin-framer@latest`
  3. Run `npm run dev` and re-open your plugin. It should now be correctly configured


### [Plugin does not support modes](https://www.framer.com/developers/troubleshooting#plugin-does-not-support-modes)
This error can happen when you attempt to launch a plugin in a specific mode from a certain context. For example when you attempt to load a plugin from a URL in the Image Picker. In this case your plugin should support either the `image` or `editImage` mode and declare it in the [Plugin Manifest](https://www.framer.com/).
### [Node Version is too Low](https://www.framer.com/developers/troubleshooting#node-version-is-too-low)
Framer uses the latest libraries for the plugin setup, which requires a modern version of node. We recommend upgrading node, or using a node version manager like `n` if you need to keep your older node version around.
