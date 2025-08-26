# [Changelog (Beta)](https://www.framer.com/developers/changelog-beta#changelog-\(beta\))
### v3.6.0
###### Aug 21, 2025
This release brings new traits to the Canvas API and plugin development workflow.
###### [Added: Layout Traits](https://www.framer.com/developers/changelog-beta#added-layout-traits)
  * Added support for layout traits, including stack, grid, padding, and gap.
  * Added support for border traits on FrameNode.
  * Added support for variant traits on FrameNode.


###### [Added: Code Mode](https://www.framer.com/developers/changelog-beta#added-code-mode)
  * Added a new `code` mode, allowing to open a Plugin in the Code Editor.


### v3.5.2
###### Jul 25, 2025
This new release introduces brand new APIs for creating menus for your plugin.
###### [Added: Menu APIs](https://www.framer.com/developers/changelog-beta#added-menu-apis)
We are introducing new APIs for creating two different types of menu:
  * lets you add a global menu to the plugin window header.
  * allows creating context menus anywhere in your plugin.


###### [Added: User APIs](https://www.framer.com/developers/changelog-beta#added-user-apis)
  * New [User](https://www.framer.com/developers/reference/plugins-user) properties: and 


  * now returns `never` instead of `Promise<void>`. That means you can treat it like a `throw`, the code that follows will not be reached. Internally `closePlugin` throws `FramerPluginClosedError`, so make sure to ignore it in your exception handlers. `framer-plugin` stops propagation of unhandled errors and rejections of this class, so you don't need to.


### v3.5.0-beta.0
###### Jul 16, 2025
This new release introduces brand new APIs for creating menus for your plugin.
###### [Added: Menu APIs](https://www.framer.com/developers/changelog-beta#added-menu-apis)
We are introducing new APIs for creating two different types of menu:
  * lets you add a global menu to the plugin window header.
  * allows creating context menus anywhere in your plugin.


  * New [User](https://www.framer.com/developers/reference/plugins-user) properties: and 


### v3.4.0
###### Jul 15, 2025
This new release adds support for Gallery fields to CMS APIs, as well as introducing support for managing code components and overrides via the new Code File API.
###### [Added: Code File API](https://www.framer.com/developers/changelog-beta#added-code-file-api)
We’ve added several new APIs to help plugin authors manage code files:
  * , , and for creating and retrieving code files 
  * `subscribeToCodeFiles[](https://www.framer.com/developers/reference/plugins-code-files-subscribe-to-code-files)` to receive notifications when code files are created or modified 
  * `codeFile.setFileContent[](https://www.framer.com/developers/reference/plugins-code-file-set-file-content)`, , and to update, rename, and delete code files 
  * `codeFile.getVersions[](https://www.framer.com/developers/reference/plugins-code-file-get-versions)` to access a file’s version history


###### [Added: Gallery Fields](https://www.framer.com/developers/changelog-beta#added-gallery-fields)
It is now possible to create and update Gallery fields, as well as set values for them when adding or updating items. This is achieved by the creation of a new `"array"` field type.
  * `ManagedCollection.setFields[](https://www.framer.com/developers/reference/plugins-managed-collection-set-fields)` and `Collection.addFields[](https://www.framer.com/developers/reference/plugins-collection-add-fields)` support creating Gallery fields.
  * `ManagedCollection.addItems[](https://www.framer.com/developers/reference/plugins-managed-collection-add-items)` and `Collection.addItems[](https://www.framer.com/developers/reference/plugins-collection-add-items)` let you add values for Gallery fields.
  * `CollectionItem.setAttributes[](https://www.framer.com/developers/reference/plugins-managed-collection-add-items)` can now update Gallery field values.


See our updated [CMS guide](https://www.framer.com/developers/cms#working-with-arrays-beta) for more information on working with arrays.
###### [Updated: Collection API](https://www.framer.com/developers/changelog-beta#updated-collection-api)
Deprecated Collection and Managed Collection `readonly` property in favor of `managedBy` and proper permission-based checks via the Permissions API
###### [Updated: User API](https://www.framer.com/developers/changelog-beta#updated-user-api)
User now has `avatarUrl` and `initials`, and is finally documented.
###### [Fixed: Draggable Component](https://www.framer.com/developers/changelog-beta#fixed-draggable-component)
Fixed the `<Draggable>` component so that the `altText` parameter is correctly applied when dragging and dropping images, ensuring accessibility metadata isn’t lost.
### v3.4.0-beta.0
###### Jul 11, 2025
This beta adds support for Gallery fields to CMS APIs, as well as introducing support for managing code components and overrides via the new Code File API.
###### [Code File API](https://www.framer.com/developers/changelog-beta#code-file-api)
We’ve added several new APIs to help plugin authors manage code files:
  * , , and for creating and retrieving code files 
  * `subscribeToCodeFiles[](https://www.framer.com/developers/reference/plugins-code-files-subscribe-to-code-files)` to receive notifications when code files are created or modified 
  * `codeFile.setFileContent[](https://www.framer.com/developers/reference/plugins-code-file-set-file-content)`, , and to update, rename, and delete code files 
  * `codeFile.getVersions[](https://www.framer.com/developers/reference/plugins-code-file-get-versions)` to access a file’s version history


###### [Gallery Fields](https://www.framer.com/developers/changelog-beta#gallery-fields)
It is now possible to create and update Gallery fields, as well as set values for them when adding or updating items. This is achieved by the creation of a new `"array"` field type.
  * `ManagedCollection.setFields[](https://www.framer.com/developers/reference/plugins-managed-collection-set-fields)` and `Collection.addFields[](https://www.framer.com/developers/reference/plugins-collection-add-fields)` support creating Gallery fields.
  * `ManagedCollection.addItems[](https://www.framer.com/developers/reference/plugins-managed-collection-add-items)` and `Collection.addItems[](https://www.framer.com/developers/reference/plugins-collection-add-items)` let you add values for Gallery fields.
  * `CollectionItem.setAttributes[](https://www.framer.com/developers/reference/plugins-managed-collection-add-items)` can now update Gallery field values.


See our updated [CMS guide](https://www.framer.com/developers/cms#working-with-arrays-beta) for more information on working with arrays.
###### [Collection API](https://www.framer.com/developers/changelog-beta#collection-api)
Deprecated Collection and Managed Collection `readonly` property in favor of `managedBy` and proper permission-based checks via the Permissions API
User now has `avatarUrl` and `initials`, and is finally documented.
### v3.3.0
###### Jun 6, 2025
  * Added support for `rem` units — allowing to set `rem` units that were announced[ in our April update](https://www.framer.com/updates/april-update-2025)
  * Added support for Vector Set nodes — these are now exposed for use in plugins
  * Improved `ManagedCollections` API — it’s now possible to call `setFields(await getFields())` without running into type errors


### v3.3.0-beta.1
###### Jun 3, 2025
  * Added support for `rem` in Text Styles
  * Allow to do `managedCollections.setFields(await managedCollections.getFields())`


### v3.3.0-beta.0
###### May 29, 2025
This release brings support for Vector Set nodes.
### v3.2.0
###### May 6, 2025
This new release introduces APIs for Redirects, which allows to manage your site Redirects programatically. Management can happen in bulk or individually.
  * Added **,****,**.
  * Added for defining order of Redirects.
  * Added class for specific redirect management.


### v3.2.0-beta.0
###### May 1, 2025
This beta release introduces APIs for Redirects, which allows to manage your site Redirects programatically. Management can happen in bulk or individually.
  * Added **,****,**.
  * Added for defining order of Redirects.
  * Added class for specific redirect management.


### v3.1.0
###### Apr 24, 2025
This release introduces two entirely new sets of APIs for Plugins: **Localization** and **Permissions**. With the new Localization APIs, Plugins are now able to programmatically read and update a site’s Locales and Localization sources. With the Permissions API, Plugins can check which permissions the Plugin user has (e.g. Design, Content-only) and adapt the Plugin functionality accordingly. Learn how to get started in the [Localization Guide](https://www.framer.com/developers/plugins-localization) and[ Permission guide](https://www.framer.com/developers/plugins-permissions).
> The `framer-plugin` package now uses a top-level await, make sure to update `vite-framer-plugin` to `1.0.7` or higher. 
###### [Localization](https://www.framer.com/developers/changelog-beta#localization)
This release introduces brand new APIs for managing your site's Localizations.
  * lets you get all your site's Locales.
  * gives you the default Locale.
  * gives you the active Locale.
  * `getLocalizationGroups[](https://www.framer.com/developers/reference/plugins-get-localization-groups)` retrives all Localization groups and sources.
  * `setLocalizationData[](https://www.framer.com/developers/reference/plugins-set-localization-data)` lets you update your site's Localization data.


We have also added Localization support to other existing APIs.
  * `Collection.getItems[](https://www.framer.com/developers/reference/plugins-collection-get-items)` now includes Localization data for each item.
  * `ManagedCollection.addItems[](https://www.framer.com/developers/reference/plugins-managed-collection-add-items)` lets you include item Localization data.
  * `Collection.addItems[](https://www.framer.com/developers/reference/plugins-collection-add-items)` lets you include item Localization data.
  * `CollectionItem.setAttributes[](https://www.framer.com/developers/reference/plugins-collection-item-set-attributes)` lets you include item Localization data.


###### [Permissions (Preview)](https://www.framer.com/developers/changelog-beta#permissions-\(preview\))
Today, Plugins can only be launched and used by those with full permissions on a Project. A few weeks from now, we’ll allow Plugins to be launched and used by those without design permissions as well. With the Permissions API Preview, we’re giving Plugin authors time to proactively accommodate for this change via these new APIs. Learn more about these flows in the [Permissions guide](https://www.framer.com/developers/plugins-permissions).
  * Calling a method unavailable to the user will result in an error.
  * lets you check methods' availability to the user.
  * `subscribeToIsAllowedTo[](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to)` lets you subscribe to changes in `isAllowedTo`.
  * is a React hook version of `subscribeToIsAllowedTo`.


  * is the ID of the field that a Collection's slug is based on.
  * [Enum Fields](https://www.framer.com/developers/reference/plugins-enum-field) can now [update](https://www.framer.com/developers/reference/plugins-enum-case-set-attributes), [remove](https://www.framer.com/developers/reference/plugins-enum-case-remove), and [sort](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order) their [Enum Cases](https://www.framer.com/developers/reference/plugins-enum-case).
  * Fields can now be marked as `required` during creation.
  * Fixed a bug where adding items with HTML content would sometimes error.
  * Fixed a bug preventing the referenced Collection of fields being updated.


  * was added as a callback to the [Draggable](https://www.framer.com/developers/reference/plugins-drag-and-drop-draggable) component.
  * `preferredImageRendering` can now be provided when adding images.


  * Fixed a bug where renaming a Text Style or Color Style would reset its path.
  * Text Styles and Color Styles now both expose their full path.


### v3.1.0-beta.3
###### Apr 11, 2025
This beta release introduces APIs for Permissions:
  * Plugins are now available to all users, not just the ones with Full Access.
  * Calling a method that is not usable by the user will result in an error.
  * lets you check methods' availability to the user.
  * `subscribeToIsAllowedTo[](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to)` lets you subscribe to changes in `isAllowedTo`.
  * is a React hook version of `subscribeToIsAllowedTo`.


Learn more with the[ Permission guide](https://www.framer.com/developers/plugins-permissions).
**Important:** Make sure to update `vite-plugin-framer` to `^1.0.7` as `framer-plugin` now uses a top-level await and won't work without it. If you don't rely on `vite-plugin-framer` then make sure you target `es2022` at the minimum. Vite targets `esnext` by default, but it might still need the following addition in its configuration:
```
optimizeDeps: { esbuildOptions: { target: "esnext" } }
```

`esnext` is a safe choice here as `optimizeDeps` is development-only.
### v3.1.0-beta.1
Breaking
###### Mar 19, 2025
This beta release brings many improvements to the Localization Beta APIs, including the ability to directly manage Localizations during the creation or updating of Collection Items, both for managed and non-managed Collections.
###### [Localization](https://www.framer.com/developers/changelog-beta#localization)
We are stabilizing these APIs and removing their `unstable_` prefix. We are also making some changes to where these APIs can be called:
  * , , and are now available in all modes.
  * `setLocalizationData[](https://www.framer.com/developers/reference/plugins-set-localization-data)` and `getLocalizationGroups[](https://www.framer.com/developers/reference/plugins-get-localization-groups)` can no longer be called from the `"configureManagedCollection"` or `"syncManagedCollection"` plugin modes.


In addition, there are some breaking changes being made to property naming:
  * `getLocalizationGroups[](https://www.framer.com/developers/reference/plugins-get-localization-groups)` now returns a instead of the previous `hiddenLocales`.
  * `setLocalizationData[](https://www.framer.com/developers/reference/plugins-set-localization-data)` now accepts a `statusByLocaleByGroup` instead of the previous `hiddenLocalesByGroup`.
  * Localization Sources now have a property instead of the previous `locales`.


###### [Collection](https://www.framer.com/developers/changelog-beta#collection)
  * When calling `ManagedCollection.addItems[](https://www.framer.com/developers/reference/plugins-managed-collection-add-items)` or `Collection.addItems[](https://www.framer.com/developers/reference/plugins-collection-add-items)`, you can now pass `statusByLocale`, and a `valueByLocale` for each field in `fieldData`.
  * When calling `Collection.getItems[](https://www.framer.com/developers/reference/plugins-collection-get-items)`, fields' values in that are localizable now have a `valueByLocale` property containing the field's Localized Values, and the item itself has a `slugByLocale` property with the slug's Localized Values.
  * Added on non-managed Collections, which returns the ID of the field the slug is based on.
  * Non-managed [Enum Fields](https://www.framer.com/developers/reference/plugins-enum-field) can now [update](https://www.framer.com/developers/reference/plugins-enum-case-set-attributes), [remove](https://www.framer.com/developers/reference/plugins-enum-case-remove), and [sort](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order) their [Enum Cases](https://www.framer.com/developers/reference/plugins-enum-case).
  * You can now pass a `required` property when creating fields, allowing them to be marked as required.
  * Fixed a bug where adding items with a Formatted Text Field that contains HTML (e.g., `<pre>` tag) would sometimes error.
  * Fixed a bug where it was not possible to update the referenced Collection of a Reference or Multi Reference Field on managed Collection.


  * Added an callback to the [Draggable](https://www.framer.com/developers/reference/plugins-drag-and-drop-draggable) component.


### v3.0.0
Breaking
###### Mar 5, 2025
Plugins version 3.0 enables entirely new functionality within CMS Plugins with a new set of APIs for modifying and adding to existing Collections that weren’t created by your Plugin (known as `UnmanagedCollection`). Along with this, we’ve made a few changes to the core CMS APIs to add stronger typing and set us up for additional features coming soon.
###### [Breaking Changes](https://www.framer.com/developers/changelog-beta#breaking-changes)
The following CMS functions now require their `fieldData` to be an object, with `value` and `type` properties. Which enforces stronger types across CMS APIs.
  * `Collection.getFields()[](https://www.framer.com/developers/reference/plugins-collection-get-fields)` now returns .
  * `BooleanField`, `StringField`, etc. are classes now.
  * `SupportedCollectionField` type has been removed.
  * `CollectionField` type has been removed.
  * `Collection.getItems()[](https://www.framer.com/developers/reference/plugins-collection-get-items)` returns typed `fieldData`.
  * `CollectionItem.setAttributes()[](https://www.framer.com/developers/reference/plugins-collection-item-set-attributes)` requires typed `fieldData`.
  * `ManagedCollection.addItems()[](https://www.framer.com/developers/reference/plugins-collection-add-items)` requires typed `fieldData`.


```
// Before 
managedCollection.addItems([
  { [fieldID]: "Your Value" }
])

// After
managedCollection.addItems([
  { [fieldID]: {
      type: "string",
      value:  "Your Value"
  }
}])
```

###### [Collections](https://www.framer.com/developers/changelog-beta#collections)
  * Plugins can now write to Collections.
  * Added `Collection.addItems()[](https://www.framer.com/developers/reference/plugins-collection-add-items)`.
  * Added `Collection.setItemOrder()[](https://www.framer.com/developers/reference/plugins-collection-set-item-order)`.
  * Added `Collection.setFieldOrder()[](https://www.framer.com/developers/reference/plugins-collection-set-field-order)`.


###### [Collection Fields](https://www.framer.com/developers/changelog-beta#collection-fields)
  * `Collection.addFields()[](https://www.framer.com/developers/reference/plugins-collection-add-fields)` lets you create new fields.
  * `Field.setAttributes()[](https://www.framer.com/developers/reference/plugins-field-set-attributes)` allows you to update the field.
  * removes the field from the Collection.
  * `Collection.removeFields()[](https://www.framer.com/developers/reference/plugins-collection-remove-fields)` removes fields in bulk.


### v2.2.0
###### Feb 11, 2025
The 2.2.0 release brings some updates to the CMS API, with a focus on improving the experience around having multiple Managed Collections created by the same Plugin.
###### [Managed Collections](https://www.framer.com/developers/changelog-beta#managed-collections)
  * Added new ⁠`getManagedCollections()` method to get all Collections managed by your Plugin.
  * Added ⁠`setAsActive()` method to select the active Collection in the Editor
  * Deprecated ⁠`getManagedCollection()` in favor of ⁠`getActiveManagedCollection()`.
  * Fixed a bug where setting Plugin Data on a `CollectionItemNode` was throwing a `Node not found` error.


###### [Collections](https://www.framer.com/developers/changelog-beta#collections)
  * Added support for ⁠`FieldDivider` type in collection fields.
  * Added ⁠`setAsActive()` method to make a collection the active one.
  * Added ⁠`removeFields()` method to remove fields by their ID.
  * Added ⁠`setFieldOrder()` method to arrange fields in a specific order.
  * Added ⁠`slugFieldName` property to Collection interface.


### v2.0.0
Breaking
###### Nov 11, 2024
The 2.0 release contains a single breaking change to the `id` field of the APIs below. Our hashing algorithm for the `id` had a higher potential for ID collisions than expected. The `id` field will now be a different hashed value for the same user/project compared to `1.x.x`. Logic that stores and compares these values will need updating. To migrate from the old value to the new value, you can reference the `apiVersion1Id` field.
  *   * 

### v1.1.0
###### Oct 15, 2024
  * Resolution support has been added to all image APIs.
  * Collection item draft status is now exposed in the API.
  * Plugin windows now support maximum width/height.


### v1.0.0
###### Oct 2, 2024
Plugins initial public release.
