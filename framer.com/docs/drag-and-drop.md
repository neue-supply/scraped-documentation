---
title: "Drag And Drop"
source: "https://www.framer.com/developers/drag-and-drop"
domain: "framer.com"
scraped_at: "2025-08-26T17:04:09.257Z"
---
# Drag And Drop
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
# [Drag & Drop](https://www.framer.com/developers/drag-and-drop#drag-drop)
You can make images, SVG, and component instances, and detached component layers draggable using the `framer.makeDraggable()` API. The function requires an HTML element as its first argument, and a function to generate the drag data as its second argument.
```javascript
const cleanup = framer.makeDraggable(div, () => {
  return {
    type: "image",
    image: "https://www.example.com/image.jpg",
    
    // Optional, used while dragging
    // Make sure to use a small image so it loads fast
    previewImage: "https://www.example.com/image.jpg",
  }
})
```

Make sure to call the returned cleanup function when you are no longer rendering the element.
## [Supported drag types](https://www.framer.com/developers/drag-and-drop#supported-drag-types)
The following data types can be inserted via dragging.
  * `image`
  * `svg`
  * `componentInstance`
  * `detachedComponentLayers`

## [Draggable](https://www.framer.com/developers/drag-and-drop#draggable)
If you are building in React we offer a `Draggable` component that makes this API simpler to work with. The component needs to be wrapped around the draggable element which can be any HTML element. It has a single `data` property. You can also pass in a function to only generate the data when requested. Make sure to only render a single element as the child. And if you want to conditionally render the draggable you have to add the condition around the outer draggable component.
```javascript
const framerIcon = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path d="M5 2.5h10v5h-5Zm0 5h5l5 5H5Zm5 5v5l-5-5Z"/></svg>`

function MyDraggableSVG() {  
  const handleClick = () => {
    void framer.addSVG({ svg: framerIcon })
  }
  
  return (
    <Draggable data={{
      type: "svg",
      svg: framerIcon,
      invertInDarkMode: true // if enabled the svg drag preview will be inverted in dark mode
    }}>
      <button onClick={handleClick}>
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20">
          <path d="M5 2.5h10v5h-5Zm0 5h5l5 5H5Zm5 5v5l-5-5Z"/>
        </svg>
      </button>
    </Draggable>
  )
}
```

## [Inserting Components](https://www.framer.com/developers/drag-and-drop#inserting-components)
You can insert components as either instances or detached layers. A component can only be inserted as detached layers when it has been created visually in Framer.
```
<Draggable
    data={{
        type: "detachedComponentLayers",
        url: "https://framer.dev/m/Hero.js@lI6PA86v8ICaqYVTRP1H",
        layout: true, // if enabled the layers will be inserted as a layout block
    }}
>
    <button
        onClick={() => {
            void framer.addDetachedComponentLayers({
                url: "https://framer.dev/m/Hero.js@lI6PA86v8ICaqYVTRP1H",
                layout: true,
            })
        }}
    >
        Layout Block
    </button>
</Draggable>
```

### [Previous Sharing ](https://www.framer.com/developers/sharing)
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
*Scraped from: https://www.framer.com/developers/drag-and-drop*