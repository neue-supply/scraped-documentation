# [Component Sharing](https://www.framer.com/developers/component-sharing#component-sharing)
All Components in Framer are built on ES Modules. This means that every Smart Component and Code Component has a unique URL that can be shared. You can paste this URL into any Framer project, directly onto the Canvas as if you are pasting an image, and the Component will appear. When pasted they will also be added to the Asset Panel for the Project if not in there already, and will periodically show an “Update” CTA when changes are made to the primary Component. 
To get the URL for your Component, find your Component under **Assets → Code** Component and right click to **“Copy URL…”**. Your clipboard will contain a URL like:
```
# Latest version
https://framer.com/m/Button-5TDo.js

# Specific version


```

The URL often has an `@` followed by a string of characters, this is known as the Version ID. This means the URL will point to the version of your component as the time of copying the URL. This is helpful if you want to keep iterating while ensuring the shared version is stable and working.
## [Preventing Unlinking](https://www.framer.com/developers/component-sharing#preventing-unlinking)
When sharing Components you may not always want people to be able to easily unlink the Code Component, as this can be confusing for people not familiar with code. You can prevent unlinking by adding the `@framerDisableUnlink` annotation to your Component. You may already be using annotations to control sizing and layout, if so you can add this annotation to the same comment. This comment must be directly above your Component code like this, with no other code in-between.
```
/**
 * @framerDisableUnlink
 *
 * @framerIntrinsicWidth 200
 * @framerIntrinsicHeight 200
 */
export default function MyComponent(props) {
  ...
```

> **Note:** Do not keep sensitive information in your Code Components as preventing unlink does not prevent your code from being seen by people with developer tool knowledge. As with any webpage, if something is rendered on the page, the code can be extracted. 
