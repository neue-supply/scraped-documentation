---
title: "Concepts"
source: "https://www.framer.com/developers/concepts"
domain: "framer.com"
scraped_at: "2025-08-26T16:56:54.763Z"
---
# Concepts
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
[Developers](https://www.framer.com/developers/)
![icon entry point for Site Search](https://framerusercontent.com/images/X8K2iCW5Tob8sQuioDPe6TJEU.png)
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
[Developers](https://www.framer.com/developers/)
![icon entry point for Site Search](https://framerusercontent.com/images/X8K2iCW5Tob8sQuioDPe6TJEU.png)
###### Search
Get Started
[Overview](https://www.framer.com/developers/)
[Compare](https://www.framer.com/developers/comparison)
[FAQ](https://www.framer.com/developers/faq)
[Plugins](https://www.framer.com/)
[Introduction](https://www.framer.com/developers/plugins-introduction)
[Quick Start](https://www.framer.com/developers/plugins-quick-start)
[Publishing](https://www.framer.com/developers/publishing)
[Changelog](https://www.framer.com/developers/changelog)
[Reference](https://www.framer.com/developers/reference)
Guides
Fetch
[Introduction](https://www.framer.com/developers/fetch-introduction)
[Examples](https://www.framer.com/developers/fetch-examples)
Components
[Introduction](https://www.framer.com/developers/components-introduction)
[Examples](https://www.framer.com/developers/component-examples)
[Sharing](https://www.framer.com/developers/component-sharing)
[Auto-Sizing](https://www.framer.com/developers/auto-sizing)
[Property Controls](https://www.framer.com/developers/property-controls)
[Reference](https://www.framer.com/developers/components-reference)
Overrides
[Introduction](https://www.framer.com/developers/overrides-introduction)
[Examples](https://www.framer.com/developers/overrides-examples)
# [Building a Plugin Interface](https://www.framer.com/developers/concepts#building-a-plugin-interface)
Plugins give you full control over the styling, allowing you to create any interface you’d like. The plugin template includes a minimal set of styles, consisting of global styles to help your plugin fit into the Framer UI.
### [Creating UI](https://www.framer.com/developers/concepts#creating-ui)
With the Plugin template many semantic HTML are styled for you already. For example a structure like the following will fit in naturally into the Framer interface by default.
```
<main>
  <hr />
  
  <input type="number" />
  <button>Add Layer</button>
</main>
```

We do not maintain an official set of reusable components, however for a more in-depth library from the community, you can try [Framer Toolbox](https://github.com/triozer/framer-toolbox) from [Cédric](https://github.com/triozer). This library includes tools and Components for elements like Segmented Controls.
  

### [Showing UI](https://www.framer.com/developers/concepts#showing-ui)
By default the UI isn't shown and only a toast appears while your plugin is running. To make the UI appear you can call `framer.showUI`. That method comes with an optional UI configuration.
```
framer.showUI({
  position: "top left", // Optional, Allowed: "top left", "center", etc.
  width: 240, // Optional
  height: 245, // Optional
  resizable: true, // Optional (default false). Allowed: true, false, "width", "height"
  minWidth: 100, // Optional
  minHeight: 100, // Optional
  maxWidth: 300, // Optional (default Infinity)
  maxHeight: 300, // Optional (default Infinity)
})
```

You can hide the UI again with the following method.
```
framer.hideUI()

// It's possible to conditionally display a UI
if (needsLogin) {
  framer.showUI()
} else {
  framer.hideUI()
}
```

To stop the plugin programmatically you can call `framer.closePlugin`. That method comes with an optional message.
```
framer.closePlugin("Image flipped successfuly", {
  variant: "success" // Optional, other options are "info" and "error"
})
```

### [Building UI](https://www.framer.com/developers/concepts#building-ui)
With the Plugin template many semantic HTML are styled for you already. For example a structure like the following will fit in naturally into the Framer interface by default.
```
<main>
  <hr />
  
  <button>Add Layer</button>
</main>
```

### [Color Tokens](https://www.framer.com/developers/concepts#color-tokens)
Framer provides a selection of CSS color variables that automatically adjust based on the light / dark mode of Framer. 
`--framer-color-tint`
`--framer-color-tint-dimmed`
`--framer-color-tint-dark`
`--framer-color-bg`
`--framer-color-bg-secondary`
`--framer-color-bg-tertiary`
`--framer-color-divider`
`--framer-color-text`
`--framer-color-text-reversed`
`--framer-color-text-secondary`
`--framer-color-text-tertiary`
### [Dark / Light Mode](https://www.framer.com/developers/concepts#dark-light-mode)
If you need to adjust more UI based on the current theme, you can use CSS rules that only apply when a specific theme is active.
```
/* Only apply in dark mode */
[data-framer-theme="dark"] .my-element {
  color: #fff;
}

/* Only apply in light mode */
[data-framer-theme="light"] .my-element {
  color: #000;
}
```

If you need to access the current theme from within your app, you can access it with the following code.
```
// Will return “light” or “dark”
document.body.dataset.framerTheme
```

### [Built-in Classes](https://www.framer.com/developers/concepts#built-in-classes)
Currently the plugin template includes a couple CSS classes for common UI in Framer.
  * `framer-button-primary` applied to a `<button />` element to make it a primary button color.
  * `framer-divider` applied to a `<div />` to be a horizontal rule.

### [Displaying Notifications](https://www.framer.com/developers/concepts#displaying-notifications)
Your Plugin can display notifications displayed to users via `framer.notify`
```javascript
const notification = framer.notify("An action was completed", {
    button: { text: "Undo", onClick: handleUndo },
    durationMs: 3000,
    onDisappear: handleDisappear,
    variant: "info", // Or 'success', 'warning', 'error'
})

// In case you want to close the notification programatically.
notification.close()

```

### [Displaying Menus](https://www.framer.com/developers/concepts#displaying-menus)
Plugins can utilize two type of menus:
  * **Header Menu** : menu always anchored to the plugin name in the top header of the plugin
  * **Context Menu** : can be shown anywhere in the plugin interface

To display a menu in the plugin header, use `framer.setMenu[](https://www.framer.com/developers/reference/plugins-set-menu)`
```
await framer.setMenu([
    {
        label: "New",
        onAction: newFile,
    },
    {
        type: "separator",
    },
    {
        label: "Log Out",
        onAction: logOut,
    },
])
```

To display a menu at any location in your plugin interface, use `framer.showContextMenu[](https://www.framer.com/developers/reference/plugins-show-context-menu)`
```
await framer.showContextMenu(
  [
    {
      label: "Edit",
      enabled: item.isEditable,
      onAction: () => editItem(item)
    },
    {
      label: "Remove",
      onAction: () => removeItem(item),
    },
  ],
  {
    location: { x: event.clientX, y: event.clientY },
  }
)
```

  

### [Previous Concepts ](https://www.framer.com/developers/concepts)### [Next Modes ](https://www.framer.com/developers/modes)
### [Previous Concepts ](https://www.framer.com/developers/concepts)### [Next Modes ](https://www.framer.com/developers/modes)
### [Previous Concepts ](https://www.framer.com/developers/concepts)### [Next Modes ](https://www.framer.com/developers/modes)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
Resources
[Desktop app ](https://www.framer.com/downloads/)
[Developers ](https://www.framer.com/developers/)
[Wallpapers ](https://www.framer.com/wallpapers/)
[Community ](https://www.framer.community/)
[Live Events ](https://www.framer.com/events/)
[Meetups ](https://www.framer.com/meetups/)
Programs
[Agencies ](https://www.framer.com/agencies/)
[Students ](https://www.framer.com/students/)
[Creators ](https://www.framer.com/creators/)
[Startups ](https://www.framer.com/startups/)
[Experts ](https://www.framer.com/expert/apply/)
[Switch ](https://www.framer.com/switch/)
Compare
[Squarespace ](https://www.framer.com/compare/framer-vs-squarespace)
[Wordpress ](https://www.framer.com/compare/framer-vs-wordpress)
[Unbounce ](https://www.framer.com/compare/framer-vs-unbounce)
[Webflow ](https://www.framer.com/compare/framer-vs-webflow)
[Figma ](https://www.framer.com/compare/framer-vs-figma)
[Wix ](https://www.framer.com/compare/framer-vs-wix)
Solutions
[Figma to HTML ](https://www.framer.com/solutions/figma-to-html/)
[Website builder ](https://www.framer.com/solutions/website-builder/)
[Portfolio maker ](https://www.framer.com/solutions/portfolio-website/)
[Landing pages ](https://www.framer.com/solutions/landing-pages/)
[UI/UX design ](https://www.framer.com/solutions/ui-ux-design/)
[No-code ](https://www.framer.com/solutions/no-code-website-builder/)
Company
[Security ](https://www.framer.com/legal/security/)
[Careers ](https://www.framer.com/careers/)
[Status ](https://www.framerstatus.com)
Abuse
[Brand ](https://www.framer.com/brand)
[Legal ](https://www.framer.com/legal/terms-of-service/)
Socials
[Instagram ](https://www.instagram.com/framer)
[YouTube ](https://www.youtube.com/@framer)
[Threads ](https://www.threads.net/@framer)
[LinkedIn ](https://www.linkedin.com/company/framer)
[TikTok ](https://www.tiktok.com/@framer)
[X ](https://x.com/framer)
[](https://www.framer.com/)
---
*Scraped from: https://www.framer.com/developers/concepts*