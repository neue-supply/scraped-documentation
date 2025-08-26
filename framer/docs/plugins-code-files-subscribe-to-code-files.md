[Reference](https://www.framer.com/developers/reference)
subscribeToCodeFiles
# subscribeToCodeFiles
Subscribe to changes in code files across the project.
```
const unsubscribe = framer.subscribeToCodeFiles((codeFiles) => {
  console.log(`Code files updated: ${codeFiles.length} total files`);
});

// Later, stop listening
unsubscribe();
```

### [Parameters](https://www.framer.com/developers/reference/plugins-code-files-subscribe-to-code-files#parameters)
  * `callback: (codeFiles: readonly CodeFile[]) => void` – Function called when code files change 


### [Returns](https://www.framer.com/developers/reference/plugins-code-files-subscribe-to-code-files#returns)
  * `Unsubscribe` – Function to stop listening to changes


