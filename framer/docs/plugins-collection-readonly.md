[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
readonly
# readonly
### readonly
Whether a Collection is read-only.
```
const collection = await framer.getActiveCollection()

if (collection.readonly) {
    framer.notify("This collection cannot be modified.", { variant: "warning" });
}
```

  * `boolean` – `true` if the Collection is read-only, `false` otherwise.


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-readonly#caveats)
  * A Collection is considered read-only if:
    * The Plugin operates in a **view-only mode** e.g. user does not have the permission to edit content.
    * The Collection is **managed by another plugin**.
    * The Collection is **in a managed collection mode** but not managed by the current Plugin.
  * Read-only Collections cannot be modified via the API.


