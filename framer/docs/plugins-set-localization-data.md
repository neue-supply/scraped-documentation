[Reference](https://www.framer.com/developers/reference)
setLocalizationData
# setLocalizationData
Update localization data.
```
await framer.unstable_setLocalizationData({
    valuesBySource: {
        [titleSourceId]: {
            [dutchLocaleId]: { action: "set", value: "Hallo Wereld" }
        }
    },
    statusByLocaleByGroup: {
        [blogPostGroupId]: {
            [dutchLocaleId]: "ready",
            [frenchLocaleId]: "excluded"
        }
    }
})
```

### [Parameters](https://www.framer.com/developers/reference/plugins-set-localization-data#parameters)
  * `update: LocalizationData` – An object representing the Localization update.
    * `valuesBySource` – Localization Source updates by Locale.
    * `statusByLocaleByGroup` – Status updates for each Locale by Localization Group.


### [ - Returns](https://www.framer.com/developers/reference/plugins-set-localization-data#returns)
  * `Promise<SetLocalizationDataResult>` – The result of the update.


