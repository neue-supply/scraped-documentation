[Reference](https://www.framer.com/developers/reference)
getManagedCollections
# getManagedCollections
### getManagedCollections
Retrieve Collections that are managed by the current Plugin.
```
const managedCollections = await framer.getManagedCollections();
```

### [Returns](https://www.framer.com/developers/reference/plugins-get-managed-collections#returns)
  * `Promise<ManagedCollection[](https://www.framer.com/developers/reference/plugins-managed-collection)[]>` – A list of Collections managed by the Plugin.


### [Caveats](https://www.framer.com/developers/reference/plugins-get-managed-collections#caveats)
  * Only Collections created or controlled by your Plugin appear in this list.
  * These Collections can be modified without the restrictions placed on user‑created Collections.


