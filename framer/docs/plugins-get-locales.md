[Reference](https://www.framer.com/developers/reference)
getLocales
# getLocales
### getLocales
Get all Locales in the project.
```
const locales = await framer.getLocales()
```

### [Returns](https://www.framer.com/developers/reference/plugins-get-locales#returns)
  * `Promise<readonly Locale[]>` – A list of all of the locales in the project.


### [Caveats](https://www.framer.com/developers/reference/plugins-get-locales#caveats)
  * Does not include the default Locale. See `getDefaultLocale[](https://www.framer.com/developers/reference/plugins-get-default-locale)`.


