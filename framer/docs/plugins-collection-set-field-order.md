[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
setFieldOrder
# setFieldOrder
Reorder the Fields in a Collection based on an array of Field IDs.
```
await collection.setFieldOrder([nameField.id, ageField.id]);
```

### [Parameters](https://www.framer.com/developers/reference/plugins-collection-set-field-order#parameters)
  * `fieldIds: string[]` – An array of Field IDs representing the desired order.


### [Returns](https://www.framer.com/developers/reference/plugins-collection-set-field-order#returns)
  * `Promise<void>`


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-set-field-order#caveats)
  * Unknown Field IDs are ignored.


