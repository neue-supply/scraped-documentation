[Reference](https://www.framer.com/developers/reference)
[CodeFile](https://www.framer.com/developers/reference/plugins-code-file)
typecheck
# typecheck
### typecheck
Run TypeScript type checking on the code file.
```
const typeErrors = await codeFile.typecheck({
  strict: true
})


```

### [Parameters](https://www.framer.com/developers/reference/plugins-typecheck#parameters)
  * `compilerOptions?: ts.server.protocol.CompilerOptions` — Optional TypeScript compiler options. See the [TypeScript CompilerOptions reference](https://www.typescriptlang.org/tsconfig) for all available options.


### [Returns](https://www.framer.com/developers/reference/plugins-typecheck#returns)
  * `Promise<TypecheckDiagnostic[](https://www.framer.com/developers/reference/plugins-typecheck-diagnostic)[]>` — An array of [TypecheckDiagnostic](https://www.framer.com/developers/reference/plugins-typecheck-diagnostic)


