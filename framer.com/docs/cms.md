---
title: "Cms"
source: "https://www.framer.com/developers/cms"
domain: "framer.com"
scraped_at: "2025-08-26T16:57:00.414Z"
---
# Cms
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
# [Working with CMS Collections](https://www.framer.com/developers/cms#working-with-cms-collections)
Plugins can read and write to the Framer CMS. Allowing you to create anything from a Notion Sync plugin, to a custom database integration, or an exporter.
![](https://i.ytimg.com/vi_webp/acFuYzW7h1Q/sddefault.webp)
Check out the video above for an overview on CMS Plugin concepts and a walkthrough of the CMS Starter Plugin. There are two kinds of ways to work with the CMS, Managed Collections and Unmanaged Collections. Unmanaged Collections are Collections in Framer that are primarily created and updated by people, whereas Managed Collections are primarily controlled by Plugins.
### [CMS Starter](https://www.framer.com/developers/cms#cms-starter)
If you’re looking to build a Plugin to sync data into Framer, the best way to get started is the CMS Starter Plugin. You can use it via the following commands:
```
// npm (recommended)
npm create framer-plugin@latest -- --starter cms

// yarn 
yarn create framer-plugin --starter cms

// pnpm
pnpm create framer-plugin --starter cms
```

### [Collections](https://www.framer.com/developers/cms#collections)
Any kind of Collection can be read from. `Collection` refers to Unmanaged Collections that are created by Users. Use the `collection` [Mode](https://www.framer.com/developers/modes) to access CMS data from your plugin.
See our [Export CSV example](https://github.com/framer/plugins/tree/main/plugins/cms-export).
```
// Get the current collection the user is viewing in the CMS.
const collection = await framer.getActiveCollection()
```

You can get a list of all the available collections.
```
await framer.getCollections()
```

When you have a reference to a specific collection, you can get its fields or items. In the CMS, fields are the columns used to define data types.
```
await framer.getFields()
```

This will return an array of objects.
```
// An example snippet from `getFields`.
[
  // ...
  {
    id: "BnNuS2i3o",
    type: "string",
    name: "Title",
  },
  {
    id: "hgNaskh4n",
    type: "boolean",
    name: "Featured",
  },
  {
    id: "JO9uOAhun",
    type: "date",
    name: "Published Date",
  },
  //...
}
```

You can also get all CMS items.
```
await framer.getItems()
```

This will return all the data in the CMS as an array of objects. Item objects contain `id`, `slug` and `fieldData`. Field data uses the field `id` as keys in an object.
  

/
```
// An example snippet from `getItems`.
[
  //...
  {
    id: "XTM8FSHGs",
    slug: "post-1",
    draft: false,
    fieldData: {
      BnNuS2i3o: "My First Post",
      hgNaskh4n: false,
      JO9uOAhun: "Wed, 15 Apr 2024 08:30:27 GMT"
    }
  },
  {
    id: "AaN8oZOpy",
    slug: "post-2",
    draft: true,
    fieldData: {
      BnNuS2i3o: "My Second Post",
      hgNaskh4n: true,
      JO9uOAhun: "Wed, 02 Aug 2024 10:13:27 GMT"
    }
  }
  //...
]

```

Supported field types:
  * **boolean** — True or false
  * **color** — A color of RGBA/HSL/HEX format
  * **number** — A number
  * **string** — Any string of text
  * **formattedText** — HTML Content. H1-H6, P and other standard content elements are supported
  * **image** — An instance of an `ImageAsset`
  * **file** — An instance of an `FileAsset`
  * **link** — URL in string format
  * **date** — A date in UTC format, or DD-MM-YYYY
  * **enum** — Requires enum case options to be defined
  * **collectionReference** — A reference to an item in another Collection
  * **multiCollectionReference** — Multiple references to items in another Collection
  * **array** — An array of fields. Currently only supports a single image field, which will create a Gallery.

There is also an **unsupported** field type. This is returned when Framer uses a field that the plugin API does not yet support.
Since field values can be many different kinds of type, always check the type before using it.
```
// Standard JavaScript type checks can be used for built-in types.
const titleField = fieldData["XTM8FSHGs"]

if (typeof titleField === "string) {
  console.log(titleField.toUpperCase())
}

// Use helpers provided by framer-plugin to check for images and files.
const assetField = fieldData["AaN8oZOpy"]

if (isImageAsset(assetField) || isFileAsset(assetField) {
  console.log(assetField.url)
}
```

### [Managed Collections](https://www.framer.com/developers/cms#managed-collections)
Managed Collections are fully controlled by the plugin. Fields and items can only be added, edited and deleted by the plugin and not the user.
Use a Managed Collection when you want to be able sync data between Framer and a third-party. See our [Notion example](https://github.com/framer/plugins/tree/main/plugins/notion).
#### [Modes](https://www.framer.com/developers/cms#modes)
Your Managed Collection plugin will only become available within the CMS when it supports both the `configureManagedCollection` and `syncManagedCollection` modes. Make sure to add these modes to the `framer.json` file. Read more on how to set this up on the [configuration page](https://www.framer.com/developers/configuration).
The active mode can be checked using `framer.mode`. When your plugin is launched with a newly created collection, the mode will be `configureManagedCollection`. In configuration mode the user expects to setup the fields and data source. 
After the initial creation step, the user can choose to open the plugin in either sync or configuration mode. For sync mode, the best experience is to not show any UI, a toast will be visible to indicate the activity of the plugin.
```
if (framer.mode === "syncManagedCollection") {
  await importData(collection, rssSourceId)
  await framer.closePlugin()
} else if (framer.mode === "configureManagedCollection") {
  framer.showUI()
}

```

#### [Getting the Managed Collection](https://www.framer.com/developers/cms#getting-the-managed-collection)
When your plugin is launched in either `configureManagedCollection` or `syncManagedCollection` mode, it can get the active collection via the `framer.getManagedCollection()`.
```javascript
const collection = await framer.getManagedCollection()
```

Once you have the Collection, there are several methods to perform common actions, such as getting the current fields, or adding items.
```
interface ManagedCollection {
    getItemIds(): Promise<string[]>
    setItemOrder(ids: string[]): Promise<void>
    getFields(): Promise<CollectionField[]>
    setFields(fields: CollectionField[]): Promise<void>
    addItems(items: CollectionItem): Promise<void>
    removeItems(ids: string[]): Promise<void>
}
```

#### [Adding Fields](https://www.framer.com/developers/cms#adding-fields)
Fields are used to defines the type of data that is added to the collection. You can configure up to 30 custom fields. 
Each custom field consists of an `id`, `name`, and `type`. For the `id` it is best to use a unique identifier that stays the same in all future synchronizations. Any change in `id` can break data assignments on the canvas the user has made.
You can change the type of a field while reusing the existing `id`, Framer will take make sure that won't result in any errors. The maximum length for an `id` is 64 characters.
```
// By using ids, fields can be renamed without breaking
// existing data assignments on the canvas.
const titleId = "Shd4oMspa"
const descriptionId = "DmV2tOwlJ"
const contentId = "eDniSM8L9"
const avatarId = "Ur2HpfEB1"

const createdAtId = "vUvFzeUxy"
const vehicleId = "ZfN0uPuHc"
const brandId = "f6gl1d2gA"
const driversId = "H46Ahd8Ad"
const galleryId = "J51ah58Aj"
const galleryImageId = "Ur2HpfEB1"

const collection = await framer.getCollection()

// Here we include all of the different field types you can use.
await collection.setFields([
    {
        id: titleId,
        name: "Title",
        type: "string",
    },
    {
        id: descriptionId,
        name: "Description",
        type: "string",
    },
    {
        id: contentId,
        name: "Content",
        type: "string",
    },
    {
        id: avatarId,
        name: "Avatar",
        type: "image",
    },
    {
        id: createdAtId,
        name: "Created At",
        type: "date",
    },
    {
        id: vehicleId,
        name: "Vehicle",
        type: "enum",
        cases: [
            { id: "1", name: "Car" },
            { id: "2", name: "Boat" },
            { id: "3", name: "Plane" },
        ],
    },
    {
        id: brandId,
        name: "Brand",
        type: "collectionReference",
        collectionId: brandsCollectionId,
    },
    {
        id: driversId,
        name: "Drivers",
        type: "multiCollectionReference",
        collectionId: driversCollectionId
    },
    // Beta
    {
        id: galleryId,
        name: "Gallery",
        type: "array",
        fields: [
          {
            id: galleryImageId,
            type: "image",
          }
        ]
    },
])
```

#### [User Editable Fields](https://www.framer.com/developers/cms#user-editable-fields)
By default, managed collection fields set by a plugin won't be editable by users using the CMS. However, there are cases where you might want a few fields edited by the user. To allow this, you can see the `userEditable` attribute.
In this example the description field can be edited by the user in the UI, the title cannot.
```
await collection.setFields([
    {
        id: titleId,
        name: "Title",
        type: "string",
    },
    {
        id: descriptionId,
        name: "Description",
        type: "string",
        userEditable: true
    },
])
```

Note that fields marked as `userEditable` can no longer have their values set by the plugin when using `addItems`. Trying to edit or add a value for an editable field will be ignored.
#### [Reference Fields](https://www.framer.com/developers/cms#reference-fields)
Fields of type `collectionReference` and `multiCollectionReference` allow you to create fields that point to items in another Collection.
In Plugins, items are referenced by slug—either a single slug for a `collectionReference` or an array of slugs for a `multiCollectionReference`.
For Managed Collections, where item IDs are controlled by the plugin, items are referenced by their ID. Note that for managed collections, you can only create references between Collections that are managed by the same Plugin.
#### [Adding Items](https://www.framer.com/developers/cms#adding-items)
Now that your fields are setup you can add items to the collection. Typically this will involve fetching data from an external resource and looping over the items to prepare them for the custom fields that were configured earlier.
Each item has a required `id` and `slug`. The data for the custom fields has to be added via `fieldData`. The `id` property for each custom field should be used as the key within the `fieldData` object.
The `addItems` method can be used for both adding new items as well as updating existing ones.
```python
import { framer, CollectionItem } from 'framer-plugin'

const collection = await framer.getCollection()
const fields = await collection.getFields()
const contentField: FormattedTextField = fields[0]

const blogPosts = await fetchBlogPosts()
const collectionItems: CollectionItem[] = []

for (const post of blogPosts) {
  collectionItems.push({
    id: post.id,
    slug: slugify(post.title),
    fieldData: {
      [titleId]: { value: post.title },
      // The key here must match the "id" value of the field
      // set in "collection.setFields". Because this field was
      // configured as "formattedText" it supports (basic) HTML.
      [contentField.id]: { value: post.content },
    }
 }) 
}

await collection.addItems(collectionItems)
```

#### [Working with Arrays](https://www.framer.com/developers/cms#working-with-arrays)
We have recently added support for our "Gallery" fields. This comes in the form of a new field type of `"array"`, which is due to Galleries being implemented in a way that is future-proof with arbitrary arrays of nested fields. At the moment, fields of type `"array"` must contain a single image field.
```javascript
const collection = await framer.getActiveCollection()

const fields = await collection.getFields()
const galleryField = fields.find((field) => field.type === "array")
const galleryImageField = galleryField.fields[0]

await collection.addItems([
  {
    id: post.id,
    slug: slugify(post.title),
    fieldData: {
      [galleryField.id]: {
        type: "array",
        value: post.images.map(image => ({
          fieldData: {
            [galleryImageField.id]: {
              type: "image",
              value: image.url,
            },
          },
        })),
      },
    },
  },
])

```

#### [Deleting Items](https://www.framer.com/developers/cms#deleting-items)
Sometimes you want to remove data from the Managed Collection. For example if certain data is no longer present in the external data source.
```javascript
const itemsIds = await collection.getItemIds()
const unseenItemIds = new Set(itemsIds)

const blogPosts = await fetchBlogPosts()
  
for (const post of blogPosts) {
  // Mark the item as seen.
  unseenItemIds.delete(post.id)
}

// Remove all items that were not seen.
const itemsToRemove = Array.from(unseenItemIds)
await collection.removeItems(itemsToRemove)
```

### [Storing metadata](https://www.framer.com/developers/cms#storing-metadata)
Similar to local storage, you can store custom data on the Managed Collection. By storing the last synchronization date, you might be able for skip some of the expensive synchronization work. But you can also store other data like the specific notion database the collection is connected to. See also the guide for [Plugin Data](https://www.framer.com/developers/storing-data).
```javascript
const lastSyncedAtStorageKey = "lastSynchronizedAt"

// Store a timestamp after a successful synchronizion.
const currentDate = new Date().toISOString()
await collection.setPluginData(lastSyncedAtStorageKey, currentDate)

// Get the last synchronization date when you start synchronizing.
const lastSynchronized = await collection.getPluginData(lastSyncedAtStorageKey)

// Skip items that were last updated before the previous synchronization.
if (lastSynchronized && post.lastUpdatedAt <= lastSynchronized) {
  continue
}
```

  

### [Previous Sites ](https://www.framer.com/developers/site)### [Next Localization ](https://www.framer.com/developers/plugins-localization)
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
*Scraped from: https://www.framer.com/developers/cms*