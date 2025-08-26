[Reference](https://www.framer.com/developers/reference)
getCodeFiles
# getCodeFiles
Get all code files in the project.
```
const allFiles = await framer.getCodeFiles();
console.log(`Project has ${allFiles.length} code files`);
```

### [Returns](https://www.framer.com/developers/reference/plugins-code-files-get-code-files#returns)
  * `Promise<readonly CodeFile[](https://www.framer.com/developers/reference/plugins-code-file)[]>` – An array of all CodeFile instances


