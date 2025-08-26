[Reference](https://www.framer.com/developers/reference)
[CodeFile](https://www.framer.com/developers/reference/plugins-code-file)
lint
# lint
### lint
Run linting on the code file content.
```
const diagnostics = await codeFile.lint({
  "forbid-browser-apis": "error"
});
```

### [Parameters](https://www.framer.com/developers/reference/plugins-code-file-lint#parameters)
  * `rules: LintConfig` — Linting rules configuration.


Whereby `LintConfig` can be
```
interface LintConfig {
  "forbid-browser-apis"?: "error" | "warning"
}
```

### [Returns](https://www.framer.com/developers/reference/plugins-code-file-lint#returns)
  * `Promise<LintDiagnostic[](https://www.framer.com/developers/reference/plugins-lint-diagnostic)[]>` — An array of [LintDiagnostic](https://www.framer.com/developers/reference/plugins-lint-diagnostic)


