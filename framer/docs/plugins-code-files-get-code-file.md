[Reference](https://www.framer.com/developers/reference)
getCodeFile
# getCodeFile
Get a specific code file by its ID.
```
const codeFile = await framer.getCodeFile("code-file-id");
console.log(`Found file: ${codeFile.name}`);
```

### [Parameters](https://www.framer.com/developers/reference/plugins-code-files-get-code-file#parameters)
  * `id: string` – The unique identifier of the code file 


### [Returns](https://www.framer.com/developers/reference/plugins-code-files-get-code-file#returns)
  * `Promise<CodeFile[](https://www.framer.com/developers/reference/plugins-code-file) | null>` – The CodeFile instance or null if not found


