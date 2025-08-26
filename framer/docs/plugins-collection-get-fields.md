[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
getFields
# getFields
Fetch all Fields in a Collection.
```
const fields = await collection.getFields();
```

### [Returns](https://www.framer.com/developers/reference/plugins-collection-get-fields#returns)
  * `Promise<Field[](https://www.framer.com/developers/reference/plugins-field)[]>` – An array of Field definitions.


### [Caveats**:**](https://www.framer.com/developers/reference/plugins-collection-get-fields#caveats)
  * Some Fields might not be fully supported by the API; unsupported Fields will be returned as an `unsupported` field type.


