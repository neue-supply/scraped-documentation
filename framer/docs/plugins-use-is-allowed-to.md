[Reference](https://www.framer.com/developers/reference)
useIsAllowedTo
# useIsAllowedTo
### useIsAllowedTo
Find out if user's permissions allow them to execute methods, in hook form.
```
const isAllowed = useIsAllowedTo("addText", "addImage")
<button disabled={!isAllowed}>+


```

### [Signature](https://www.framer.com/developers/reference/plugins-use-is-allowed-to#signature)
```
useIsAllowedTo: (
  ...methods: [ProtectedMethod, ...ProtectedMethod[]]
) => boolean
```

### [Parameters](https://www.framer.com/developers/reference/plugins-use-is-allowed-to#parameters)
  * `methods` – The methods to check, at least one.


### [Returns](https://www.framer.com/developers/reference/plugins-use-is-allowed-to#returns)
  * `boolean` – `true` if all of `methods` can be executed, `false` otherwise.


Learn more with the[ Permission guide](https://www.framer.com/developers/plugins-permissions).
