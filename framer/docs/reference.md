# API Reference
A list of all functions and attributes available on the `framer` Plugin API.
## [Plugin UI](https://www.framer.com/developers/reference#plugin-ui)
A set of functions for opening and closing the Plugin itself, along with options setting a specific size for your Plugin. Plugins are able to run completely UI-less if desired.
###  [closePlugin](https://www.framer.com/developers/reference/plugins-close-plugin)
Close and terminate the plugin.
Hide the plugin window.
Register a global plugin menu.
###  [showContextMenu](https://www.framer.com/developers/reference/plugins-show-context-menu)
Show a context menu at a given location.
Show the plugin window.
## [User APIs](https://www.framer.com/developers/reference#user-apis)
###  [getCurrentUser](https://www.framer.com/developers/reference/plugins-get-current-user)
Information about the user that's interacting with the plugin.
A Framer user.
A Framer user.
###  [apiVersion1Id](https://www.framer.com/developers/reference/plugins-user-api-version-1-id)
Deprecated, use id.
###  [avatarUrl](https://www.framer.com/developers/reference/plugins-user-avatar-url)
Full URL of user's profile picture, if they have one.
User's ID, represented as a 64-lowercase-character hexadecimal string.
2-uppercase-character acronym of user's name, for when there is no avatar.
User's full name.
## [Code File API](https://www.framer.com/developers/reference#code-file-api)
The CodeFile API allows plugins to create, read, update, and manage code files within a Framer project. A code file exports either [overrides](https://www.framer.com/developers/overrides-examples) or [code components](https://www.framer.com/developers/components-introduction).
###  [createCodeFile](https://www.framer.com/developers/reference/plugins-code-files-create-code-file)
Create a new code file in the project.
###  [getCodeFile](https://www.framer.com/developers/reference/plugins-code-files-get-code-file)
Get a specific code file by its ID.
###  [getCodeFiles](https://www.framer.com/developers/reference/plugins-code-files-get-code-files)
Get all code files in the project.
###  [subscribeToCodeFiles](https://www.framer.com/developers/reference/plugins-code-files-subscribe-to-code-files)
Subscribe to changes in code files across the project.
A class representing a code file in a Framer project.
A class representing a code file in a Framer project.
The current content/source code of the file.
Array of exports available in this code file.
###  [getVersions](https://www.framer.com/developers/reference/plugins-code-file-get-versions)
Get all versions/history of this code file.
The unique identifier of the code file.
Run linting on the code file content.
The name of the code file (e.g., "MyComponent.tsx").
The file system path of the code file.
Remove the code file from the project.
Rename the code file.
###  [setFileContent](https://www.framer.com/developers/reference/plugins-code-file-set-file-content)
Set the content of the code file.
###  [typecheck](https://www.framer.com/developers/reference/plugins-typecheck)
Run TypeScript type checking on the code file.
###  [CodeFileExport](https://www.framer.com/developers/reference/plugins-code-file-export)
Union type representing exports from a code file.
Union type representing exports from a code file.
URL for inserting the component
###  [isDefaultExport](https://www.framer.com/developers/reference/plugins-code-file-export-is-default-export)
Whether this is a default export
Export name
Discriminator
###  [CodeFileVersion](https://www.framer.com/developers/reference/plugins-code-file-version)
Represents a historical version of a code file.
Represents a historical version of a code file.
The creation timestamp.
The user that created this version.
###  [getContent](https://www.framer.com/developers/reference/plugins-code-file-version-get-content)
Retrieve content for this version.
The version identifier.
The file name at this version.
## [Canvas APIs](https://www.framer.com/developers/reference#canvas-apis)
Framer provides APIs to interact with our Canvas. These APIs range from directly editing Nodes, to Images, and Drag & Drop. Learn more about Nodes in our [guide](https://www.framer.com/developers/nodes).
###  [Drag & Drop](https://www.framer.com/developers/reference/plugins-drag-and-drop)
Allow any HTML element to become draggable.
Allow any HTML element to become draggable.
An object that represents the data to be dragged.
###  [Draggable](https://www.framer.com/developers/reference/plugins-drag-and-drop-draggable)
A React component that makes it's child draggable.
###  [onDragComplete](https://www.framer.com/developers/reference/plugins-drag-and-drop-on-drag-complete)
A callback triggered when a drag finishes.
###  [makeDraggable](https://www.framer.com/developers/reference/plugins-make-draggable)
Allow any HTML element to become draggable.
Allow to get or edit node.
Allow to get or edit node.
###  [aspectRatio](https://www.framer.com/developers/reference/plugins-traits-aspect-ratio)
Width-to-height ratio
###  [backgroundColor](https://www.framer.com/developers/reference/plugins-traits-background-color)
Background color in RGBA format or as a ColorStyle instance
###  [backgroundGradient](https://www.framer.com/developers/reference/plugins-traits-background-gradient)
Background gradient
###  [backgroundImage](https://www.framer.com/developers/reference/plugins-traits-background-image)
Background image asset
Border properties
###  [borderRadius](https://www.framer.com/developers/reference/plugins-traits-border-radius)
Border radius for rounded corners
Distance from bottom edge when using absolute/fixed positioning
Center anchor position as percentage
Center anchor position as percentage
###  [collectionId](https://www.framer.com/developers/reference/plugins-traits-collection-id)
Collection ID for the web page
###  [componentIdentifier](https://www.framer.com/developers/reference/plugins-traits-component-identifier)
Identifier of the component
###  [componentName](https://www.framer.com/developers/reference/plugins-traits-component-name)
Name of the component
Property control values for code components
Font selection for text
Spacing between items in a layout
Gesture state for component variants
###  [gridAlignment](https://www.framer.com/developers/reference/plugins-traits-grid-alignment)
How items are aligned within the grid
###  [gridColumnCount](https://www.framer.com/developers/reference/plugins-traits-grid-column-count)
Number of columns in the grid
###  [gridColumnMinWidth](https://www.framer.com/developers/reference/plugins-traits-grid-column-min-width)
Minimum width of grid columns in pixels
###  [gridColumnWidth](https://www.framer.com/developers/reference/plugins-traits-grid-column-width)
Width of grid columns in pixels
###  [gridColumnWidthType](https://www.framer.com/developers/reference/plugins-traits-grid-column-width-type)
Type of column width sizing
###  [gridItemColumnSpan](https://www.framer.com/developers/reference/plugins-traits-grid-item-column-span)
Number of columns to span
###  [gridItemFillCellHeight](https://www.framer.com/developers/reference/plugins-traits-grid-item-fill-cell-height)
Whether to fill the grid cell height
###  [gridItemFillCellWidth](https://www.framer.com/developers/reference/plugins-traits-grid-item-fill-cell-width)
Whether to fill the grid cell width
###  [gridItemHorizontalAlignment](https://www.framer.com/developers/reference/plugins-traits-grid-item-horizontal-alignment)
Horizontal alignment within grid cell
###  [gridItemRowSpan](https://www.framer.com/developers/reference/plugins-traits-grid-item-row-span)
Number of rows to span
###  [gridItemVerticalAlignment](https://www.framer.com/developers/reference/plugins-traits-grid-item-vertical-alignment)
Vertical alignment within grid cell
###  [gridRowCount](https://www.framer.com/developers/reference/plugins-traits-grid-row-count)
Number of rows in the grid
###  [gridRowHeight](https://www.framer.com/developers/reference/plugins-traits-grid-row-height)
Height of grid rows in pixels
###  [gridRowHeightType](https://www.framer.com/developers/reference/plugins-traits-grid-row-height-type)
Type of row height sizing
Height of the node
###  [imageRendering](https://www.framer.com/developers/reference/plugins-traits-image-rendering)
How images should be rendered when scaled
###  [inheritsFromId](https://www.framer.com/developers/reference/plugins-traits-inherits-from-id)
ID of the node this variant inherits from
###  [inlineTextStyle](https://www.framer.com/developers/reference/plugins-traits-inline-text-style)
Apply a text style preset
###  [isBreakpoint](https://www.framer.com/developers/reference/plugins-traits-is-breakpoint)
Whether this is a breakpoint
###  [isPrimaryBreakpoint](https://www.framer.com/developers/reference/plugins-traits-is-primary-breakpoint)
Whether this is the primary breakpoint
###  [isPrimaryVariant](https://www.framer.com/developers/reference/plugins-traits-is-primary-variant)
Whether this is the primary variant
###  [isVariant](https://www.framer.com/developers/reference/plugins-traits-is-variant)
Whether this is a component variant
Enables stack or grid layout
Distance from left edge when using absolute/fixed positioning
URL or internal page link
###  [linkOpenInNewTab](https://www.framer.com/developers/reference/plugins-traits-link-open-in-new-tab)
Whether to open link in new tab
Whether the node is locked for editing
###  [maxHeight](https://www.framer.com/developers/reference/plugins-traits-max-height)
Maximum height constraint
Maximum width constraint
###  [minHeight](https://www.framer.com/developers/reference/plugins-traits-min-height)
Minimum height constraint
Minimum width constraint
The name of the node displayed in the layers panel
Opacity of the node
Inner spacing of a container with layout
URL path for the web page
Positioning behavior of the node
Distance from right edge when using absolute/fixed positioning
Rotation angle in degrees
###  [stackAlignment](https://www.framer.com/developers/reference/plugins-traits-stack-alignment)
How items are aligned perpendicular to the stack direction
###  [stackDirection](https://www.framer.com/developers/reference/plugins-traits-stack-direction)
Direction of items in a stack layout
###  [stackDistribution](https://www.framer.com/developers/reference/plugins-traits-stack-distribution)
How items are distributed in a stack layout
###  [stackWrapEnabled](https://www.framer.com/developers/reference/plugins-traits-stack-wrap-enabled)
Whether items should wrap to the next line
SVG markup content
Distance from top edge when using absolute/fixed positioning
Whether the node is visible on the canvas
Width of the node
## [CMS APIs](https://www.framer.com/developers/reference#cms-apis)
Framer provides APIs to interact with our CMS. Collections can be either user-created (`Unmanaged`) or controlled by a Plugin (`Managed`). The Collection types share similar API structures and Plugin authors can choose which Collection type works best for their use-case. Reference the latest APIs below or learn more with the [CMS guide](https://www.framer.com/developers/cms).
###  [getActiveCollection](https://www.framer.com/developers/reference/plugins-get-active-collection)
Retrieve the Collection currently active (selected) in the Framer UI.
###  [getActiveManagedCollection](https://www.framer.com/developers/reference/plugins-get-active-managed-collection)
Retrieve the currently active managed Collection from the UI.
###  [getCollections](https://www.framer.com/developers/reference/plugins-get-collections)
Get all Collections in the project. Both Managed and Unmanaged.
###  [getManagedCollections](https://www.framer.com/developers/reference/plugins-get-managed-collections)
Retrieve Collections that are managed by the current Plugin.
###  [Collection](https://www.framer.com/developers/reference/plugins-collection)
A Collection that is not controlled by a Plugin.
A Collection that is not controlled by a Plugin.
###  [addFields](https://www.framer.com/developers/reference/plugins-collection-add-fields)
Create new unmanaged Collection fields.
Add new Items to a Collection.
###  [getFields](https://www.framer.com/developers/reference/plugins-collection-get-fields)
Fetch all Fields in a Collection.
Retrieve all Items within a Collection.
###  [managedBy](https://www.framer.com/developers/reference/plugins-collection-managedby)
Returns who manages the Collection
Whether a Collection is read-only.
###  [removeFields](https://www.framer.com/developers/reference/plugins-collection-remove-fields)
Remove fields from a Collection by their IDs.
###  [removeItems](https://www.framer.com/developers/reference/plugins-collection-remove-items)
Remove Items from a Collection by their IDs.
###  [setAsActive](https://www.framer.com/developers/reference/plugins-collection-set-as-active)
Set the Collection as active.
###  [setFieldOrder](https://www.framer.com/developers/reference/plugins-collection-set-field-order)
Reorder the Fields in a Collection based on an array of Field IDs.
###  [setItemOrder](https://www.framer.com/developers/reference/plugins-collection-set-item-order)
Reorder the Items in a Collection based on an array of Item IDs.
###  [slugFieldBasedOn](https://www.framer.com/developers/reference/plugins-collection-slug-field-based-on)
The ID of the Field the slug is based on.
###  [slugFieldName](https://www.framer.com/developers/reference/plugins-collection-slug-field-name)
The name of the Field used as the slug.
###  [CollectionItem](https://www.framer.com/developers/reference/plugins-collection-item)
A class for a CMS item in a Collection or ManagedCollection.
A class for a CMS item in a Collection or ManagedCollection.
###  [fieldData](https://www.framer.com/developers/reference/plugins-collection-item-field-data)
The fields and corresponding values of the Collection item.
A unique identifier for a Collection item.
Remove the item from the Collection.
###  [setAttributes](https://www.framer.com/developers/reference/plugins-collection-item-set-attributes)
Set the values of the fields of the CMS item.
Slug value of the CMS item.
An Enum Case for an Enum Field.
An Enum Case for an Enum Field.
A unique identifier for the Enum Case.
The name of the Enum Case.
###  [nameByLocale](https://www.framer.com/developers/reference/plugins-enum-case-name-by-locale)
Localized values for the name of the Enum Case.
Remove the Enum Case.
###  [setAttributes](https://www.framer.com/developers/reference/plugins-enum-case-set-attributes)
Update the attributes of the Enum Case.
###  [EnumField](https://www.framer.com/developers/reference/plugins-enum-field)
An enum field.
An enum field.
An Enum Case for an Enum Field.
Add an Enum Case.
The cases of the Enum Field.
###  [setCaseOrder](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order)
Set the order of the Enum Field's Enum Cases.
###  [ManagedCollection](https://www.framer.com/developers/reference/plugins-managed-collection)
A CMS Collection that is controlled by a Plugin.
A CMS Collection that is controlled by a Plugin.
Add new items or update existing ones if their IDs match.
Get all fields on the Collection.
###  [getItemIds](https://www.framer.com/developers/reference/plugins-managed-collection-get-items-ids)
Retrieve all Item IDs in a Managed Collection.
###  [removeItems](https://www.framer.com/developers/reference/plugins-managed-collection-remove-items)
Remove CMS items by their ID.
###  [setAsActive](https://www.framer.com/developers/reference/plugins-managed-collection-set-as-active)
Open this Collection in the Editor.
Add, update, or remove Collection fields.
###  [setItemOrder](https://www.framer.com/developers/reference/plugins-managed-collection-set-item-order)
Arrange CMS items in a specific order.
## [Localization API](https://www.framer.com/developers/reference#localization-api)
Framer provides APIs to interact with our Localization functionality. The key pieces of Localization in Framer are**Locales** , **Localization Groups** , and **Localization Sources**. Locales are a language paired with an optional region, like English or English (Canada). Localization groups are things like pages or CMS items that contain one or more Localization sources. Localization sources are the strings from your site, along with their localized values.
###  [getActiveLocale](https://www.framer.com/developers/reference/plugins-get-active-locale)
Get the currently active Locale.
###  [getDefaultLocale](https://www.framer.com/developers/reference/plugins-get-default-locale)
Get the default locale of the project.
###  [getLocales](https://www.framer.com/developers/reference/plugins-get-locales)
Get all Locales in the project.
###  [getLocalizationGroups](https://www.framer.com/developers/reference/plugins-get-localization-groups)
Get all Localization Groups in the project.
###  [setLocalizationData](https://www.framer.com/developers/reference/plugins-set-localization-data)
Update localization data.
A Locale in your project.
A Locale in your project.
The language code of the Locale.
###  [fallbackLocaleId](https://www.framer.com/developers/reference/plugins-locale-fallback-locale-id)
The ID of the fallback Locale.
A unique identifier for a Locale.
The name of the Locale.
Slug value of the Locale.
###  [LocalizationGroup](https://www.framer.com/developers/reference/plugins-localization-group)
A group of Localization Sources.
A group of Localization Sources.
A unique identifier for a Localization Group.
The name of a Localization Group.
The Localization Sources in the Localization Group.
###  [statusByLocale](https://www.framer.com/developers/reference/plugins-localization-group-status-by-locale)
The status of the Localization Group in each Locale.
###  [supportsExcludedStatus](https://www.framer.com/developers/reference/plugins-localization-group-supports-excluded-status)
Whether a Localization Group supports the "excluded" status.
The type of a Localization Group.
###  [LocalizationSource](https://www.framer.com/developers/reference/plugins-localization-source)
A localizable string on your site.
###  [LocalizationSource](https://www.framer.com/developers/reference/plugins-localization-source)
A localizable string on your site.
A localizable string on your site.
A unique identifier for a Localization Source.
The name of a Localization Source.
The type of value for this Localization Source.
The current value of the Localization Source in the default locale.
###  [valueByLocale](https://www.framer.com/developers/reference/plugins-localization-source-value-by-locale)
Localized values and metadata for each Locale.
###  [LocalizationValue](https://www.framer.com/developers/reference/plugins-localization-value)
The localized value and associated metadata for a Locale.
###  [LocalizationValue](https://www.framer.com/developers/reference/plugins-localization-value)
The localized value and associated metadata for a Locale.
The localized value and associated metadata for a Locale.
###  [lastEdited](https://www.framer.com/developers/reference/plugins-localization-value-last-edited)
The time the Localized Value was last edited at.
Whether the value is read only and therefore cannot be updated.
The status of the Localization Value.
The actual text of the Localization Value
A warning about the Localization Value.
## [Settings APIs](https://www.framer.com/developers/reference#settings-apis)
Framer provides APIs to interact with our Site Settings functionality. **Redirects** , currently the primary feature supported by these APIs, allow you to permanently route traffic from an old path to a new URL.
###  [addRedirects](https://www.framer.com/developers/reference/plugins-redirects-add-redirects)
Add Redirects to your project.
###  [getRedirects](https://www.framer.com/developers/reference/plugins-redirects-get-redirects)
Get all Redirects in the project.
###  [removeRedirects](https://www.framer.com/developers/reference/plugins-redirects-remove-redirects)
Remove Redirects from your project.
###  [setRedirectOrder](https://www.framer.com/developers/reference/plugins-redirects-set-redirect-order)
Sets the order of the Redirects in the list
###  [Redirect](https://www.framer.com/developers/reference/plugins-redirect)
A redirect from one path to another.
A redirect from one path to another.
###  [expandToAllLocales](https://www.framer.com/developers/reference/plugins-redirect-expand-to-all-locales)
Whether the Redirect is expanded to all locales.
The source path of the Redirect.
A unique identifier for the Redirect.
Remove the redirect.
###  [setAttributes](https://www.framer.com/developers/reference/plugins-redirect-set-attributes)
Set the attributes of a Redirect.
The destination path of the Redirect.
## [Permissions](https://www.framer.com/developers/reference#permissions)
Plugins can do only what the user can. These APIs let you find out if the methods you need are available to the user, and potentially disable certain functions of your Plugin if not. Learn more with the[ Permission guide](https://www.framer.com/developers/plugins-permissions).
###  [isAllowedTo](https://www.framer.com/developers/reference/plugins-is-allowed-to)
Find out if user's permissions allow them to execute methods.
###  [subscribeToIsAllowedTo](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to)
Subscribe to changes in whether the user is allowed to execute methods.
###  [useIsAllowedTo](https://www.framer.com/developers/reference/plugins-use-is-allowed-to)
Find out if user's permissions allow them to execute methods, in hook form.
A property with the current mode. Modes are used to understand the context in which the Plugin is being run, and adjust logic as needed. Learn more in the [mode guide](https://www.framer.com/developers/modes).
## [Project](https://www.framer.com/developers/reference#project)
Information about the current Framer Project. Returns the display name of the Project as well as a hashed Project ID. This ID cannot be used to access the Project.
##### [`getProjectInfo()`](https://www.framer.com/developers/reference#getprojectinfo\(\))
## [Selection](https://www.framer.com/developers/reference#selection)
Functions for reading, setting, or listening to the current selection on the Canvas. The returned list can range from zero items to a very large list of items.
##### [`getSelection()`](https://www.framer.com/developers/reference#getselection\(\))
##### [`setSelection(nodeIds)`](https://www.framer.com/developers/reference#setselection\(nodeids\))
##### [`subscribeToSelection(callback)`](https://www.framer.com/developers/reference#subscribetoselection\(callback\))
```
const [selection, setSelection] = useState<CanvasNode[]>([])

useEffect(() => {
    return framer.subscribeToSelection(setSelection)
}, [])

console.log(`Selected ${selection.length} item(s)`)


```

## [Assets](https://www.framer.com/developers/reference#assets)
A selection of functions for working with Images, Files, and SVGs. The high-level `add` and `set` functions are designed to work in most cases and automatically handle uploading for you. Learn more in the [working with Assets guide](https://www.framer.com/developers/assets).
##### [`addImage(imageAsset)`](https://www.framer.com/developers/reference#addimage\(imageasset\))
##### [`setImage(imageAsset)`](https://www.framer.com/developers/reference#setimage\(imageasset\))
##### [`uploadImage(file)`](https://www.framer.com/developers/reference#uploadimage\(file\))
##### [`uploadFile(file)`](https://www.framer.com/developers/reference#uploadfile\(file\))
##### [`uploadFiles(files[])`](https://www.framer.com/developers/reference#uploadfiles\(files-\))
##### [`addSvg(svgString)`](https://www.framer.com/developers/reference#addsvg\(svgstring\))
## [Components](https://www.framer.com/developers/reference#components)
Functions for utilising Components in your Plugin. Learn more in the [Component guide](https://www.framer.com/developers/plugins-with-components).
##### [`addComponentInstance({ url, attributes })`](https://www.framer.com/developers/reference#addcomponentinstance\(-url-attributes-\))
##### [`addDetachedComponentLayers({ url, layout, attributes })`](https://www.framer.com/developers/reference#adddetachedcomponentlayers\(-url-layout-attributes-\))
A selection of functions for working with text layers and their content. 
##### [`setText(text)`](https://www.framer.com/developers/reference#settext\(text\))
##### [`addText(text)`](https://www.framer.com/developers/reference#addtext\(text\))
##### [`subscribeToText(callback)`](https://www.framer.com/developers/reference#subscribetotext\(callback\))
## [Custom Code](https://www.framer.com/developers/reference#custom-code)
With Custom Code your plugin can install code snippets in a user's Website via `<script>` tags. Custom Code added by a Plugin appears in a separate section of a Project’s site settings specifically for Plugins. This can be used to load external scripts on a site. Custom code should be valid HTML. 
##### [`setCustomCode(options)`](https://www.framer.com/developers/reference#setcustomcode\(options\))
##### [`getCustomCode()`](https://www.framer.com/developers/reference#getcustomcode\(\))
##### [`subscribeToCustomCode(callback)`](https://www.framer.com/developers/reference#subscribetocustomcode\(callback\))
When setting Custom Code, you must provide the html string, as well as a `location`. 
```
framer.setCustomCode({ 
  html: '<script src="https://example.com/script.js"></script>',
  location: "bodyEnd" 
})
```

The `location` property has the following values:
  * `headStart` - Injects the code snippet at the start of the HTML `<head>` tag
  * `headEnd` - Injects the code snippet at the end of the HTML `<head>` tag
  * `bodyStart` - Injects the code snippet at the start of the `<body>` tag
  * `bodyEnd` - injects the code snippet at the end of the `<body>` tag


Setting the `html` value back to `null` clears the installed code snippet.
```
framer.setCustomCode({ 
  html: null,
  location: "bodyEnd" 
})
```

## [Storing Data](https://www.framer.com/developers/reference#storing-data)
Functions for storing data that your Plugin case use across users and sessions. Learn about the different ways to store data in our [Data guide](https://www.framer.com/developers/storing-data).
##### [`getPluginData(key)`](https://www.framer.com/developers/reference#getplugindata\(key\))
##### [`setPluginData(key, value)`](https://www.framer.com/developers/reference#setplugindata\(key-value\))
##### [`getPluginDataKeys()`](https://www.framer.com/developers/reference#getplugindatakeys\(\))
## [Styles](https://www.framer.com/developers/reference#styles)
A set of functions for creating, reading and manipulating the Color and Text Styles in a Project. Learn more in our [Styles guide](https://www.framer.com/developers/styles).
##### [`createColorStyle(attributes)`](https://www.framer.com/developers/reference#createcolorstyle\(attributes\))
##### [`getColorStyle(id)`](https://www.framer.com/developers/reference#getcolorstyle\(id\))
##### [`getColorStyles()`](https://www.framer.com/developers/reference#getcolorstyles\(\))
##### [`subscribeToColorStyles(callback)`](https://www.framer.com/developers/reference#subscribetocolorstyles\(callback\))
##### [`createTextStyle(attributes)`](https://www.framer.com/developers/reference#createtextstyle\(attributes\))
##### [`getTextStyle(id)`](https://www.framer.com/developers/reference#gettextstyle\(id\))
##### [`getTextStyles()`](https://www.framer.com/developers/reference#gettextstyles\(\))
##### [`subscribeToTextStyles(callback)`](https://www.framer.com/developers/reference#subscribetotextstyles\(callback\))
Plugins can use typefaces available in the Font Picker to get information about specific fonts or to apply them to [Text Styles](https://www.framer.com/developers/styles). 
##### [`getFont(family)`](https://www.framer.com/developers/reference#getfont\(family\))
##### [`getFonts()`](https://www.framer.com/developers/reference#getfonts\(\))
Unlike the Font Picker, which groups fonts by typeface, `getFonts` will list individual fonts for each weight and style. You can think these as separate font files.
```
await framer.getFonts()

[
  //..
  {
    family: "Inter",
    weight: 900,
    style: "normal"
  },
  {
    family: "Noto Sans",
    weight: 400,
    style: "normal"
  },
  //..
]
```

To get a specific font from a family, use `getFont` and pass in the family name. This is **not** case sensitive. By default, this will return a font in the family that has a normal weight and style.
```
// Get Noto Sans with a weight of 400 in a normal style.
const font = await framer.getFont("Noto Sans")

// Get Noto Sans with a weight of 800 in an italic style.
const font = await framer.getFont("Noto Sans", {
  weight: 800,
  style: "italic"
})
```

Make sure to check that a font exists before using it. If a font does not exist, `getFont` will return `null`. 
> **Note:** Custom Fonts are not available to Plugins 
## [Editor](https://www.framer.com/developers/reference#editor)
Functions for common actions in the Framer Editor, like going to a specific node on the canvas, or displaying a message in a toast. 
##### [`zoomIntoView(nodeId)`](https://www.framer.com/developers/reference#zoomintoview\(nodeid\))
##### [`notify(message, options?: NotifyOptions)`](https://www.framer.com/developers/reference#notify\(message-options-notifyoptions\))
You can automatically adjust the viewport's pan and zoom so that a node appears in the center. This is the equivalent to using **Zoom to Selection** in the UI, except you can use any list of Nodes.
```
// Scroll and zoom the viewport to show a specific node.
await framer.zoomIntoView("node-id")

// Scroll and zoom to fit multiple nodes into the viewport.
await framer.zoomIntoView(["node-id-1", "node-id-2"])
```

Low-level API for working with Nodes. Useful for doing very specific tasks that may not be covered by the higher-level APIs. Learn more in our [working with Nodes guide](https://www.framer.com/developers/nodes).
##### [`createFrameNode(attributes)`](https://www.framer.com/developers/reference#createframenode\(attributes\))
##### [`cloneNode(nodeId)`](https://www.framer.com/developers/reference#clonenode\(nodeid\))
##### [`removeNode(nodeId)`](https://www.framer.com/developers/reference#removenode\(nodeid\))
##### [`getCanvasRoot()`](https://www.framer.com/developers/reference#getcanvasroot\(\))
##### [`subscribeToCanvasRoot(callback)`](https://www.framer.com/developers/reference#subscribetocanvasroot\(callback\))
##### [`getNode(nodeId)`](https://www.framer.com/developers/reference#getnode\(nodeid\))
##### [`getParent(nodeId)`](https://www.framer.com/developers/reference#getparent\(nodeid\))
##### [`getChildren(nodeId)`](https://www.framer.com/developers/reference#getchildren\(nodeid\))
##### [`getRect(nodeId)`](https://www.framer.com/developers/reference#getrect\(nodeid\))
##### [`setAttributes(nodeId, attributes)`](https://www.framer.com/developers/reference#setattributes\(nodeid-attributes\))
##### [`setParent(nodeId, parentId)`](https://www.framer.com/developers/reference#setparent\(nodeid-parentid\))
##### [`getNodesWithType(type)`](https://www.framer.com/developers/reference#getnodeswithtype\(type\))
##### [`getNodesWithAttribute(attribute)`](https://www.framer.com/developers/reference#getnodeswithattribute\(attribute\))
##### [`getNodesWithAttributeSet(attribute)`](https://www.framer.com/developers/reference#getnodeswithattributeset\(attribute\))
