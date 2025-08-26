[Reference](https://www.framer.com/developers/reference)
Traits
# Traits
Allow to get or edit node.
Traits represent the various properties and behaviors that can be applied to nodes in Framer. Each node type supports a specific set of traits that define its appearance, layout, and behavior.
###### [Null Values](https://www.framer.com/developers/reference/plugins-traits#null-values)
Setting a trait to `null` generally removes or resets that property:
  * `backgroundColor: null` - Removes the background color
  * `layout: null` - Disables any applied layout (stack or grid)
  * `borderRadius: null` - Removes border radius
  * `border: null` - Disables the border


###### [CSS Dimensions](https://www.framer.com/developers/reference/plugins-traits#css-dimensions)
Many traits use CSS dimension values with specific units:
  * `px` - Pixels (e.g., `"100px"`)
  * `%` - Percentage (e.g., `"50%"`)
  * `fr` - Fraction (for grid/stack layouts, e.g., `"1fr"`)
  * `vh` - Viewport height (e.g., `"100vh"`)


## [Node Type Support Matrix](https://www.framer.com/developers/reference/plugins-traits#node-type-support-matrix)
Trait | FrameNode | TextNode | SVGNode | ComponentInstanceNode | ComponentNode | WebPageNode | VectorSetNode | VectorSetItemNode  
---|---|---|---|---|---|---|---|---  
**Basic Properties**  
name  
visible  
locked  
**Visual Properties**  
backgroundColor  
backgroundImage  
backgroundGradient  
opacity  
rotation  
borderRadius  
border  
imageRendering  
**Position & Layout**  
position  
top/right/bottom/left  
centerX/centerY  
width/height  
Size Constraints  
aspectRatio  
**Layout System**  
layout  
gap  
padding  
Stack Properties  
Grid Properties  
Grid Item Properties  
**Type-Specific**  
svg  
font  
inlineTextStyle  
link  
linkOpenInNewTab  
controls  
**Component Properties**  
componentIdentifier  
componentName  
isVariant  
isBreakpoint  
**Web Page**  
path  
collectionId  
##### Methods & Properties
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
###  [controls](https://www.framer.com/developers/reference/plugins-traits-controls)
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
###  [maxWidth](https://www.framer.com/developers/reference/plugins-traits-max-width)
Maximum width constraint
###  [minHeight](https://www.framer.com/developers/reference/plugins-traits-min-height)
Minimum height constraint
###  [minWidth](https://www.framer.com/developers/reference/plugins-traits-min-width)
Minimum width constraint
The name of the node displayed in the layers panel
Opacity of the node
Inner spacing of a container with layout
URL path for the web page
###  [position](https://www.framer.com/developers/reference/plugins-traits-position)
Positioning behavior of the node
Distance from right edge when using absolute/fixed positioning
###  [rotation](https://www.framer.com/developers/reference/plugins-traits-rotation)
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
