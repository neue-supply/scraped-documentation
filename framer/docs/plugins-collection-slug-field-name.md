[Reference](https://www.framer.com/developers/reference)
[Collection](https://www.framer.com/developers/reference/plugins-collection)
slugFieldName
# slugFieldName
### slugFieldName
The name of the Field used as the slug.
```
const slugField = collection.slugFieldName;
```

  * `string | null` – The slug Field name or `null` if not defined.


### [Caveats](https://www.framer.com/developers/reference/plugins-collection-slug-field-name#caveats)
  * Only Collections that are not managed by a Plugin will have this value set.
  * Operations that rely on slugs may fail if the slug Field is not set.


