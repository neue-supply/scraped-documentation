[Reference](https://www.framer.com/developers/reference)
createCodeFile
# createCodeFile
Create a new code file in the project.
```
const newFile = await framer.createCodeFile(
  "MyComponent",
  `export default function MyComponent() {
    return <div>Hello World</div>
  }`
);
```

### [Parameters](https://www.framer.com/developers/reference/plugins-code-files-create-code-file#parameters)
  * `name: string` — The name of the file to create
  * `code: string` — The initial content of the file


### [Returns](https://www.framer.com/developers/reference/plugins-code-files-create-code-file#returns)
  * `Promise<CodeFile[](https://www.framer.com/developers/reference/plugins-code-file)>` – The created CodeFile instance


