[Reference](https://www.framer.com/developers/reference)
[EnumCase](https://www.framer.com/developers/reference/plugins-enum-case)
setAttributes
# setAttributes
### setAttributes
Update the attributes of the Enum Case.
```
enumCase.setAttributes({
  name: "New Name",
  nameByLocale: { 
    nl: { action: "set", value: "Nieuwe naam"}
  }
})
```

### [Parameters](https://www.framer.com/developers/reference/plugins-enum-case-set-attributes#parameters)
  * `attributes: UpdateEnumCase` – An array of the IDs of all Enum Cases, in the desired new order.
    * `name` – The name of the Enum Case.
    * `nameByLocale` - Localization updates for Locales.


### [Returns](https://www.framer.com/developers/reference/plugins-enum-case-set-attributes#returns)
  * `Promise<EnumCase | null>`


