[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
getItems
# getItems
### getItems
Retrieve all Items within a Collection.
```
const items = await collection.getItems();
```

### [Returns](https://www.framer.com/developers/reference/plugins-collection-get-items#returns)
  * `Promise<CollectionItem[](https://www.framer.com/developers/reference/plugins-collection-item)[]>` – An array of Collection Items.


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-get-items#caveats)
  * Items may include drafts (unpublished Items).


