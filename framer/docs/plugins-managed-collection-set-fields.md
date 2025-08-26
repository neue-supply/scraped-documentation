[Reference](https://www.framer.com/developers/reference)
[ManagedCollection](https://www.framer.com/developers/reference/plugins-managed-collection)
setFields
# setFields
### setFields
Add, update, or remove Collection fields.
```
await collection.setFields([
  {
    id: "1",
    type: "string",
    name: "Name"
  },
  {
    id: "2",
    type: "number",
    name: "Age"
  },
])
```

### [Parameters](https://www.framer.com/developers/reference/plugins-managed-collection-set-fields#parameters)
  * `fields: ManagedCollectionFieldSetInput[]` – The array of fields that should be used for the collection


### [Returns](https://www.framer.com/developers/reference/plugins-managed-collection-set-fields#returns)
  * `Promise<void>`


