[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
managedBy
# managedBy
### managedBy
Returns who manages the Collection
```
const collection = await framer.getActiveCollection()

if (framer.mode === "collection" && collection.managedBy !== "user") {
    framer.notify("This Collection cannot be modified.", { variant: "warning" });
}
```

  * `string` – Returns who manages the Collection:
    * `user` if the Collection is user-created.
    * `thisPlugin` if the Collection is managed by the current Plugin.
    * `anotherPlugin` if the Collection is managed by another Plugin.


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-managedby#caveats)
  * Plugin still needs to check if a user have the Permission to edit content via `framer.isAllowedTo[](https://www.framer.com/developers/reference/plugins-is-allowed-to)`.


