[Reference](https://www.framer.com/developers/reference)
[LocalizationGroup](https://www.framer.com/developers/reference/plugins-localization-group)
statusByLocale
# statusByLocale
### statusByLocale
The status of the Localization Group in each Locale.
`LocalizationGroupStatusByLocale`
A Localization Group can have a different status in each Locale. For example, you may want to show a blog post in your French Locale, but exclude it in your Dutch Locale.
```
type LocalizationGroupStatus = "excluded" | "ready"
type LocalizationGroupStatusByLocale = Record<LocaleId,


```

