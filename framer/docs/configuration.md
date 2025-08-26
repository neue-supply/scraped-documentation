# [Configuration](https://www.framer.com/developers/configuration#configuration)
Every plugin should define a `framer.json` file that describes the configuration for the plugin. This file is automatically created for you in the root of the directory after running `npm create framer-plugin`. 
You can extend or modify this file to change the configuration of your plugin, for example to support a different Plugin [Mode](https://www.framer.com/), or to change the icon and name of your plugin.
```
{
  "id": "xxxxxx",
  "name": "My Plugin",
  "modes": [
    "canvas",
    "image", // Allows launching plugins from the Image Popout
    "editImage", // Allows launching plugins from the Image Popout when an image is set
  ],
  "icon": "/icon.svg" // Change the icon of your image. Relative to your plugin `public` folder 
}
```

In the Framer interface, your Plugin name will almost always be shown alongside an icon. This is a 30x30 image or SVG that lives within your Plugins “public” folder, and configured in your `framer.json` with the `icon` field. The border radius will be applied automatically in the Framer interface. 
If using an SVG, make sure it is designed at 30x30 size. If using an image, we recommend providing an image with a size of 90px by 90px and running through an optimiser such as [Squoosh](https://squoosh.app/).
