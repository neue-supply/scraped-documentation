[Reference](https://www.framer.com/developers/reference)
[CodeFile](https://www.framer.com/developers/reference/plugins-code-file)
getVersions
# getVersions
### getVersions
Get all versions/history of this code file.
```
const versions = await codeFile.getVersions();
console.log(`File has ${versions.length} versions`);
```

### [Returns](https://www.framer.com/developers/reference/plugins-code-file-get-versions#returns)
  * `Promise<readonly CodeFileVersion[](https://www.framer.com/developers/reference/plugins-code-file-version)[]>` — An array of [CodeFileVersion](https://www.framer.com/developers/reference/plugins-code-file-version) instances


