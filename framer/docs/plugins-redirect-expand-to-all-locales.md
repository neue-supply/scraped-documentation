[Reference](https://www.framer.com/developers/reference)
[Redirect](https://www.framer.com/developers/reference/plugins-redirect)
expandToAllLocales
# expandToAllLocales
### expandToAllLocales
Whether the Redirect is expanded to all locales.
`boolean`
When a Redirect is expanded to all Locales, the Redirect will apply not only in the base Locale, but also in all other Locales in the project. 
For example, for a project with a Spanish Locale, the following would Redirect both `/business` to `/enterprise`, and `/es/business` to `/es/enterprise`:
```
await framer.addRedirects([
  { from: "/business", to: "/enterprise", expandToAllLocales: true }
])
```

