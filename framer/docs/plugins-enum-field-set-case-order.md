[Reference](https://www.framer.com/developers/reference)
[EnumField](https://www.framer.com/developers/reference/plugins-enum-field)
setCaseOrder
# setCaseOrder
### setCaseOrder
Set the order of the Enum Field's Enum Cases.
```
const alphabeticalCaseOrder = enumField.cases
    .toSorted((a, b) => a.name.localeCompare(b.name))
    .map(({ id }) => id)
await enumField.setCaseOrder(alphabeticalCaseOrder)
```

### [Parameters](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order#parameters)
  * `caseIds: string[]` – An array of the IDs of all Enum Cases, in the desired new order.


### [Returns](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order#returns)
  * `Promise<void>`


