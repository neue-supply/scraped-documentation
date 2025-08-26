[Reference](https://www.framer.com/developers/reference)
getActiveLocale
# getActiveLocale
### getActiveLocale
Get the currently active Locale.
```
const activeLocale = await framer.getActiveLocale()
```

### [Returns](https://www.framer.com/developers/reference/plugins-get-active-locale#returns)
  * `Promise<Locale>` – The currently active Locale.


### [Caveats](https://www.framer.com/developers/reference/plugins-get-active-locale#caveats)
  * In "localization" mode, the active locale is the locale selected in the Localizations panel.
  * In "canvas" mode, the active locale is the locale selected in the toolbar, or the default locale.


