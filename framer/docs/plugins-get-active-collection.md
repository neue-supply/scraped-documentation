[Reference](https://www.framer.com/developers/reference)
getActiveCollection
# getActiveCollection
Retrieve the Collection currently active (selected) in the Framer UI.
```
const collection = await framer.getActiveCollection();
```

### [Returns](https://www.framer.com/developers/reference/plugins-get-active-collection#returns)
  * `Promise<Collection[](https://www.framer.com/developers/reference/plugins-collection) | null>` – The active Collection or `null` if none is selected.


### [Caveats](https://www.framer.com/developers/reference/plugins-get-active-collection#caveats)
  * If the active Collection is managed by a Plugin, you may want to use `getActiveManagedCollection()[](https://www.framer.com/developers/reference/plugins-get-active-managed-collection)` instead.
  * The selection may change if the user interacts with the UI.


