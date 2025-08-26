[Reference](https://www.framer.com/developers/reference)
subscribeToIsAllowedTo
# subscribeToIsAllowedTo
### subscribeToIsAllowedTo
Subscribe to changes in whether the user is allowed to execute methods.
```
console.log(`Initial: ${framer.isAllowedTo("addText")}`)
const unsub = framer.subscribeToIsAllowedTo("addText", (isAllowed) => {
    console.log(`New: ${isAllowed}`)
    unsub()
})
```

### [Signature](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to#signature)
```
subscribeToIsAllowedTo: (
  ...args: [
    ...methods: [ProtectedMethod, ...ProtectedMethod[]],
    callback: (isAllowed: boolean) => void,
  ]
) => Unsubscribe;
```

### [Parameters](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to#parameters)
  * `methods` – The methods to check, at least one.
  * `callback` – The function that's called every time `isAllowed` changes, where `isAllowed` is `true` if all of `methods` can be executed, and `false` otherwise.


### [Returns](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to#returns)
  * `Unsubscribe` – The function to call to unsubscribe.


Learn more with the[ Permission guide](https://www.framer.com/developers/plugins-permissions).
