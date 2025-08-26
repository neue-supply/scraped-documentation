[Reference](https://www.framer.com/developers/reference)
[ManagedCollection](https://www.framer.com/developers/reference/plugins-managed-collection)
addItems
# addItems
### addItems
Add new items or update existing ones if their IDs match.
```
await collection.addItems([
    {
        id: "1",
        slug: "item-1",
        fieldData: {
            [nameField.id]: { type: "string", value: "Eric" },
            [ageField.id]: { type: "number", value: 47 },
        },
    },
])
```

> **Important** : currently, calling `addItems` with existing item ids merges the provided field data with the existing items' current field data, meaning any omitted fields remain unchanged.
> In version 4.0.0, this behavior will change - calling `addItems` with existing item ids will **fully replace** those items with the provided field data, meaning any fields not explicitly included will be **removed**. For example, if you initially add an item with a `name` field and an `age` field, and later call `addItems` again with the same id but only provide the `name` field, the previously set `age` field will be removed.
> To avoid unexpected behaviour when migrating between 3.X.X and 4.0.0, **always** include all fields when updating existing items.
### [Parameters](https://www.framer.com/developers/reference/plugins-managed-collection-add-items#parameters)
  * `items: ManagedCollectionItemInput[]` – An array of Items to add or update.


### [Returns](https://www.framer.com/developers/reference/plugins-managed-collection-add-items#returns)
  * `Promise<void>`


