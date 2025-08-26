[Reference](https://www.framer.com/developers/reference)
isAllowedTo
# isAllowedTo
Find out if user's permissions allow them to execute methods.
```
const isAllowed = framer.isAllowedTo("addText", "addImage")
```

### [Signature](https://www.framer.com/developers/reference/plugins-is-allowed-to#signature)
```
isAllowedTo: (
  ...methods: [ProtectedMethod, ...ProtectedMethod[]]
) => boolean
```

### [Parameters](https://www.framer.com/developers/reference/plugins-is-allowed-to#parameters)
  * `methods` – The methods to check, at least one.


### [Returns](https://www.framer.com/developers/reference/plugins-is-allowed-to#returns)
  * `boolean` – `true` if all of `methods` can be executed, `false` otherwise.


Learn more with the[ Permission guide](https://www.framer.com/developers/plugins-permissions).
