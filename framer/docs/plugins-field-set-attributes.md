[Reference](https://www.framer.com/developers/reference)
setAttributes
# setAttributes
Set the attributes of a Collection field.
```
const updatedField = await field.setAttributes({ name: "Better Name" })

if (field.type === "file") {
  const updatedField = await field.setAttributes({ allowedFileTypes: ["mdx"] })
}
```

### [Params](https://www.framer.com/developers/reference/plugins-field-set-attributes#params)
  * `attributes: UpdateFieldAttributes<typeof field>` – The updated attributes for the field.


### [Returns](https://www.framer.com/developers/reference/plugins-field-set-attributes#returns)
  * `Promise<typeof field | null>`


### [Caveats](https://www.framer.com/developers/reference/plugins-field-set-attributes#caveats)
  * May return `null` if the field was deleted before this method was called.


