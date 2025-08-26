[Reference](https://www.framer.com/developers/reference)
[CollectionItem](https://www.framer.com/developers/reference/plugins-collection-item)
setAttributes
# setAttributes
### setAttributes
Set the values of the fields of the CMS item.
```
const updatedCollectionItem = await collectionItem.setAttributes({
    slug: "new-slug",
    fieldData: {
        [ageField.id]: { type: "number", 48 },
    },
})
```

### [Params](https://www.framer.com/developers/reference/plugins-collection-item-set-attributes#params)
  * `update: EditableCollectionItemAttributes` – The updated attributes for the collection item.


### [Returns](https://www.framer.com/developers/reference/plugins-collection-item-set-attributes#returns)
  * `Promise<CollectionItem | null>`


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-item-set-attributes#caveats)
  * May return `null` if the item was deleted before this method was called.


