[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
setItemOrder
# setItemOrder
### setItemOrder
Reorder the Items in a Collection based on an array of Item IDs.
```
await collection.setItemOrder([item3.id, item1.id, item2.id])
```

### [Parameters](https://www.framer.com/developers/reference/plugins-collection-set-item-order#parameters)
  * `itemsIds: string[]` – An array of Item IDs representing the desired order.


### [Returns](https://www.framer.com/developers/reference/plugins-collection-set-item-order#returns)
  * `Promise<void>`


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-set-item-order#caveats)
  * Unknown Item IDs are ignored.


