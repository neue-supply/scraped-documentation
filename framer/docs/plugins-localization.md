# [Localization](https://www.framer.com/developers/plugins-localization#localization)
This guide focuses on the core workflows of the Localization Plugin APIs, enabling you to programmatically manage your Localizations in Framer. This flexible set of APIs enables you to build anything from syncing to external services, to programmatically editing your Site’s Localizations, and more.
## [Concepts](https://www.framer.com/developers/plugins-localization#concepts)
The key pieces of Localization in Framer are**Locales** , **Localization Groups** , and **Localization Sources**. Locales are a language paired with an optional region, like English or English (Canada). Localization groups are things like pages or CMS items that contain one or more Localization sources. Localization sources are the strings from your site, along with their localized value.
## [Examples](https://www.framer.com/developers/plugins-localization#examples)
The core part of this API is the getting and setting of Localization sources for the Locales in the project. The following is a basic example of updating every Localization Source for the word “Hello” within the French Locale.
```
// Find Locale to update
const locales = await framer.getLocales()
const frenchLocale = locales.find(locale => locale.code === "fr")

// Filter specific sources to update
const groups = await framer.getLocalizationGroups()

// Collect changes in localization data object
const localizationData: LocalizationData = { valuesBySource: {} }

// Update French localization for all matching sources
for (const group of groups) {
  for (const source of group.sources) {
    if (source.value === "Hello") {
        localizationData.valuesBySource[source.id] = {
          [frenchLocale.id]: { action: "set", value: "Bonjour" }
        }
    }
  }
}

await framer.setLocalizationData(localizationData)
```

It is also possible to toggle whether a groups is excluded in Locales. The following shows how you can, for example, exclude all collection items in the French Locale.
```
const statusByLocaleByGroup: LocalizationData["statusByLocaleByGroup"] = {}

for (const group of groups) {
  if (group.type === "collection-item") {
    statusByLocaleByGroup[group.id] = { [frenchLocale.id]: "excluded" }
  }
}

await framer.setLocalizationData({ statusByLocaleByGroup })
```

To make it easier to manage Localization when working with Collections, we have also added the ability to update Localization Sources when adding or updating Collection Items. The following shows how to directly supply localized values and control Locale status when creating a Collection Item.
```
await collectionItem.addItems([
    {
        id: "1",
        slug: "item-1",
        fieldData: {
            [nameField.id]: {
              type: "string",
              value: "John",
              valueByLocale: {
                [frenchLocale.id]: { action: "set", value: "Jean" }
              }
            },
            [imageField.id]: {
              type: "image",
              value: imageUrl,
              alt: "Image Description",
              altByLocale: {
                [frenchLocale.id]: { action: "set", value: "Description de l'image" }
              }
            },
        },
        statusByLocale: {
          [frenchLocale.id]: "ready",
          [dutchLocale.id]: "excluded",
        }
    },
])
```

These concepts can be extended to achieve a wide range of functionality within Plugins. For a more complete example using these APIs, you can browse our example Locale Sync Plugin code [in our open source Plugins repo](https://github.com/framer/plugins/tree/main/plugins/locale-sync).
Please see our [reference documentation](https://www.framer.com/developers/reference) for more information about these APIs.
