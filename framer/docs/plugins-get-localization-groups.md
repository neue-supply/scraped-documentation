[Reference](https://www.framer.com/developers/reference)
getLocalizationGroups
# getLocalizationGroups
### getLocalizationGroups
Get all Localization Groups in the project.
```
const groups = await framer.getLocalizationGroups()

for (const group of groups) {
    console.log(`Group: ${group.name}`)

    for (const source of group.sources) {
        console.log(`Source: ${source.value}`)

        for (const [localeId, value] of Object.entries(source.valueByLocale) {
            console.log(`Localized Value for ${localeId}: ${value.value}`)
        }
    }
}
```

### [Returns](https://www.framer.com/developers/reference/plugins-get-localization-groups#returns)
  * ``Promise<readonly LocalizationGroup[](https://www.framer.com/developers/reference/plugins-localization-group)[]>` – All Localization Groups in the project.


