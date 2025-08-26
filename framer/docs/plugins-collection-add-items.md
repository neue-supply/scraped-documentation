[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
addItems
# addItems
### addItems
Add new Items to a Collection.
```
await collection.addItems([
    { 
      slug: "eric",
      fieldData: {
        [nameField.id]: { type: "string", value: "Eric" },
        [ageField.id]: { type: "number", value: 47 },
      } 
    }
]);
```

### [Parameters](https://www.framer.com/developers/reference/plugins-collection-add-items#parameters)
  * `items: CollectionItemInput[]` – An array of Items to add or update.


### [Returns](https://www.framer.com/developers/reference/plugins-collection-add-items#returns)
  * `Promise<void>`


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-add-items#caveats)
  * If an `id` is provided and matches an existing Item, that Item will be updated.
  * Items without an `id` are created as new records.
  * `slug` should be unique.


