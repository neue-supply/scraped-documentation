[Reference](https://www.framer.com/developers/reference)
[EnumField](https://www.framer.com/developers/reference/plugins-enum-field)
addCase
# addCase
### addCase
Add an Enum Case.
```
await enumField.addCase({ 
  name: "Name",
  nameByLocale: { 
    nl: { action: "set", value: "Naam"}
  }
})
```

### [Parameters](https://www.framer.com/developers/reference/plugins-enum-field-add-case#parameters)
  * `attributes: CreateEnumCase` – An object representing the Enum Case.
    * `name` – The name of the Enum Case.
    * `nameByLocale` - Localization updates for Locales.


### [ - Returns](https://www.framer.com/developers/reference/plugins-enum-field-add-case#returns)
  * `Promise<EnumCase[](https://www.framer.com/developers/reference/plugins-enum-case)>` – The added Enum Case.


