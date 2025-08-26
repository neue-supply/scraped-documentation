[Reference](https://www.framer.com/developers/reference)
type
# type
### type
The type of a Collection field.
```
| "boolean"
| "color"
| "number"
| "string"
| "formattedText"
| "image"
| "link"
| "date"
| "file"
| "enum"
| "collectionReference"
| "multiCollectionReference"
| "divider"
| "unsupported"
```

Use it to discriminate the `Field` union like so:
```
field.allowedFileTypes.join(", ") // TypeScript error

if (field.type === "file") {
  field.allowedFileTypes.join(", ") // Success
}
```

