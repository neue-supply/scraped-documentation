[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
addFields
# addFields
### addFields
Create new unmanaged Collection fields.
```
const createdFields = await collection.addFields([
  { type: "string", name: "Name" },
  { type: "enum", name: "Status", cases: [{ name: "New" }, { name: "Done" }] },
  { type: "file", name: "Text", allowedFileTypes: ["md"] },
  { type: "collectionReference", name: "Author", collectionId: "ASh5SZOh" },
])
```

### [Parameters](https://www.framer.com/developers/reference/plugins-collection-add-fields#parameters)
  * `fields: CreateField[]` – The array of fields that should be added to the collection.


### [Returns](https://www.framer.com/developers/reference/plugins-collection-add-fields#returns)
  * `Promise<Field[](https://www.framer.com/developers/reference/plugins-field)[]>` – The created fields.


### [Related](https://www.framer.com/developers/reference/plugins-collection-add-fields#related)
```
type CreateField =
  | { type: "boolean", name: string }
  | { type: "color", name: string }
  | { type: "number", name: string }
  | { type: "string", name: string }
  | { type: "formattedText", name: string }
  | { type: "image", name: string }
  | { type: "link", name: string }
  | { type: "date", name: string }
  | { type: "file", name: string, allowedFileTypes: string[] }
  | { type: "enum", name: string, cases: { name: string }[] }
  | { type: "collectionReference", name: string, collectionId: string }
  | { type: "multiCollectionReference", name: string, collectionId: string }
  | { type: "divider", name: string }
```

