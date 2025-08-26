[Reference](https://www.framer.com/developers/reference)
EnumField
# EnumField
### EnumField
An enum field.
```
const fields = await collection.getFields()
const enumField = fields.find(field => field.type === "enum")

for (const enumCase of enumField.cases) {
    if (enumCase.name === replaceTerm) {
        // Updating a case
        enumCase.setAttributes({ name: replacement })
    } else if (enumCase.name === removalTerm) {
        // Removing a case
        enumCase.remove()
    }
}

// Adding a case
await enumField.addCase({ name: "Bonus" })

// Sorting all cases
const alphabeticalCaseOrder = enumField.cases
    .toSorted((a, b) => a.name.localeCompare(b.name))
    .map(({ id }) => id)
await enumField.setCaseOrder(alphabeticalCaseOrder)
```

##### Methods & Properties
Add an Enum Case.
Add an Enum Case.
The cases of the Enum Field.
The cases of the Enum Field.
###  [setCaseOrder](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order)
Set the order of the Enum Field's Enum Cases.
###  [setCaseOrder](https://www.framer.com/developers/reference/plugins-enum-field-set-case-order)
Set the order of the Enum Field's Enum Cases.
