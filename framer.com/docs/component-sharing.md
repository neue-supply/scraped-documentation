---
title: "Component Sharing"
source: "https://www.framer.com/developers/component-sharing"
domain: "framer.com"
scraped_at: "2025-08-26T17:04:23.117Z"
---
# Component Sharing
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
# [Auto-Sizing](https://www.framer.com/developers/component-sharing#auto-sizing)
Framer has the ability to accurately measure any content on the canvas. When building code components, this means you can write styles as you are used to on the web and Framer will figure out the rest.
### [Defining Component Size](https://www.framer.com/developers/component-sharing#defining-component-size)
There are four settings for code component layout in Framer: `auto`, `fixed`, `any`, and `any-prefer-fixed`. These can be set for width or height axis individually, using `@framerSupportedLayoutWidth` and `@framerSupportedLayoutHeight` annotations.
  * `auto` — The component will dictate its own size based on its content.
  * `fixed` — The component is in a fixed size container and can fill 100% of its size.
  * `any` — Users can switch between auto and fixed sizing via the properties panel.
  * `any-prefer-fixed` — The same as the previous option, but set tofixed by default.

### [Specifying Options](https://www.framer.com/developers/component-sharing#specifying-options)
The default layout setting for all components in Framer is `any`. To select different layout options for your component you'll need to add an annotation. This annotation is a `special comment` that Framer reads and uses to accordingly set options for your component. **Make sure this comment is on the lines directly above where you declare your component.**
The following code will make your component have auto-sizing for width, but not height. You can make these two properties any combination of sizing options as long as you have both width & height specified at all times.
```
/**
* @framerSupportedLayoutWidth auto
* @framerSupportedLayoutHeight fixed
*/
export function Toggle(props) { ...
```

### [Intrinsic Size](https://www.framer.com/developers/component-sharing#intrinsic-size)
These annotations let Framer know what size your component should be inserted into the canvas when fixed sizing is enabled. In this case, it will insert with a width of 200px and a height of 200px.
```
/**
* @framerIntrinsicHeight 200
* @framerIntrinsicWidth 200
*/
export function Box(props) { ...
```

### [Using Auto-Sizing](https://www.framer.com/developers/component-sharing#using-auto-sizing)
Now, let’s make a title prop that is configurable from the interface (we will explain more about property controls later).
### [Supporting the default any](https://www.framer.com/developers/component-sharing#supporting-the-default-any)
By spreading the style prop into your parent container style properties with `{...style}`, Framer will override the width and height when auto-sizing is turned off (`fixed` sizing) by passing down `{ width: "100%", height: "100%" }` via the style prop. While doing this, Framer wraps your component in a fixed-sized container set to the user-defined size on the canvas.
```
export function Toggle(props) {
    return <div style={{ width: 50, height: 50 }} />
}
```

### [Auto-Sizing Dynamically](https://www.framer.com/developers/component-sharing#auto-sizing-dynamically)
If you want to auto-size your component based on logic or state changes, using a `useLayoutEffect` will work best with our measuring system. Generally, you'll want to use this approach when controlling internal state from outside the component.
```python
import { addPropertyControls, ControlType } from "framer"
import { useState, useEffect, useLayoutEffect } from "react"

/*
 * @framerSupportedLayoutWidth auto
 * @framerSupportedLayoutHeight auto
 */
export default function Test(props) {
    const start = 0
    const [count, setCount] = useState(0)
    
    useLayoutEffect(() => {
        if (start !== count) setCount(start)
    }, [start])
    
    return (
        <div
            style={{ ...containerStyle }}
            onClick={() => {
                setCount(count + 1)
            }}
        >
            {new Array(count).fill(1, 0, count).map((_, index) => {
                return <div style={squareStyle}>{index}</div>
            })}
        </div>
    )
}

const containerStyle = {
    display: "flex",
    justifyContent: "center",
    alignItems: "center",
    overflow: "hidden",
}

const squareStyle = {
    margin: 10,
    padding: 50,
    color: "white",
    fontWeight: 600,
    borderRadius: 25,
    backgroundColor: "#09F",
    width: "max-content",
    whiteSpace: "pre-wrap",
    flexShrink: 0,
}
```

### [Measuring Absolute Height Width Values](https://www.framer.com/developers/component-sharing#measuring-absolute-height-width-values)
Sometimes when writing components, you may want to know the size of the component in pixels. To do this, you will need to measure the component with a [resizeObserver](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver). We have a hook for this you can import called `useMeasuredSize`. Be careful, as any measurement like this will reduce the performance of your site, as well as your canvas.
```python
import { useMeasuredSize } from "https://framer.com/m/framer/useMeasuredSize.js"

/**
* @framerSupportedLayoutWidth fixed
* @framerSupportedLayoutHeight any
*/
export function ScaledToggle(props) {
  const { style, tint } = props
  
  const container = useRef<HTMLDivElement>()
  const size = useMeasuredSize(container)
  const width = size?.width ?? 50
  const height = size?.height ?? 50

  return (
      <motion.div
        initial={false}
        ref={container}
        animate={{ backgroundColor: tint }}
        style={{ width: 50, height: width * 0.5,  ...style }}
      />
    )
}
```

### [Previous Sharing ](https://www.framer.com/developers/component-sharing)### [Next Property Controls ](https://www.framer.com/developers/property-controls)
### [Previous Sharing ](https://www.framer.com/developers/component-sharing)### [Next Property Controls ](https://www.framer.com/developers/property-controls)
### [Previous Sharing ](https://www.framer.com/developers/component-sharing)### [Next Property Controls ](https://www.framer.com/developers/property-controls)
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
*Scraped from: https://www.framer.com/developers/component-sharing*