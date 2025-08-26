---
title: "Configuration"
source: "https://www.framer.com/developers/configuration"
domain: "framer.com"
scraped_at: "2025-08-26T16:57:19.152Z"
---
# Configuration
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

### [Icons](https://www.framer.com/developers/configuration#icons)
In the Framer interface, your Plugin name will almost always be shown alongside an icon. This is a 30x30 image or SVG that lives within your Plugins “public” folder, and configured in your `framer.json` with the `icon` field. The border radius will be applied automatically in the Framer interface. 
![](https://framerusercontent.com/images/XBBD6l4qkvAs2xBaimKBIBsneg.png?width=1400&height=600)
If using an SVG, make sure it is designed at 30x30 size. If using an image, we recommend providing an image with a size of 90px by 90px and running through an optimiser such as [Squoosh](https://squoosh.app/).
### [Previous Custom Code ](https://www.framer.com/developers/custom-code)
### [Previous Custom Code ](https://www.framer.com/developers/custom-code)
### [Previous Custom Code ](https://www.framer.com/developers/custom-code)
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
*Scraped from: https://www.framer.com/developers/configuration*