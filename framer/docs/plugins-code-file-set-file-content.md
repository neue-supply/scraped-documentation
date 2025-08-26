[Reference](https://www.framer.com/developers/reference)
[CodeFile](https://www.framer.com/developers/reference/plugins-code-file)
setFileContent
# setFileContent
### setFileContent
Set the content of the code file.
```
const updatedFile = await codeFile.setFileContent(`
export default function MyComponent() {
  return <div>Hello World</div>
}
`);
```

### [Parameters](https://www.framer.com/developers/reference/plugins-code-file-set-file-content#parameters)
  * `code: string` — The new source code content.


### [Returns](https://www.framer.com/developers/reference/plugins-code-file-set-file-content#returns)
  * `Promise<CodeFile[](https://www.framer.com/developers/reference/plugins-code-file)>`


