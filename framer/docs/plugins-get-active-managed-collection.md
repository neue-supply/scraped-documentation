[Reference](https://www.framer.com/developers/reference)
getActiveManagedCollection
# getActiveManagedCollection
Retrieve the currently active managed Collection from the UI.
```
const collection = await framer.getActiveManagedCollection();
```

### [Returns](https://www.framer.com/developers/reference/plugins-get-active-managed-collection#returns)
  * `Promise<ManagedCollection[](https://www.framer.com/developers/reference/plugins-managed-collection) | null>` – The active managed Collection or `null` if none is active.


### [Caveats](https://www.framer.com/developers/reference/plugins-get-active-managed-collection#caveats)
  * Only applies when the Plugin is operating in a mode that supports managed Collections.
  * When no managed Collection is active, this method returns `null`.


