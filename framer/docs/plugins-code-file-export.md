[Reference](https://www.framer.com/developers/reference)
CodeFileExport
# CodeFileExport
### CodeFileExport
Union type representing exports from a code file.
A discriminated union type representing exports from a code file. The `type` property determines the shape:
  * If `type` is `"component"`, this export represents a Framer component and includes an `insertURL` for insertion.
  * If `type` is `"override"`, this export represents a property override.


##### Methods & Properties
###  [insertURL](https://www.framer.com/developers/reference/plugins-code-file-export-insert-url)
URL for inserting the component
###  [insertURL](https://www.framer.com/developers/reference/plugins-code-file-export-insert-url)
URL for inserting the component
###  [isDefaultExport](https://www.framer.com/developers/reference/plugins-code-file-export-is-default-export)
Whether this is a default export
###  [isDefaultExport](https://www.framer.com/developers/reference/plugins-code-file-export-is-default-export)
Whether this is a default export
Export name
Export name
Discriminator
Discriminator
