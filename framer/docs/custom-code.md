# [Custom Code](https://www.framer.com/developers/custom-code#custom-code)
With Custom Code your plugin can install code snippets in a user's Website via `<script>` tags. This can be used to load external scripts on a site. Custom code should be valid HTML.
### [Inserting custom code](https://www.framer.com/developers/custom-code#inserting-custom-code)
```
framer.setCustomCode({ 
  html: '<script src="https://example.com/script.js"></script>',
  location: "bodyEnd" 
})
```

The example above inserts a `<script>` tag at the end of the `<body>` tag in the resulting HTML.
The `location` property has the following values:
  * `headStart` - Injects the code snippet at the start of the HTML `<head>` tag
  * `headEnd` - Injects the code snippet at the end of the HTML `<head>` tag
  * `bodyStart` - Injects the code snippet at the start of the `<body>` tag
  * `bodyEnd` - injects the code snippet at the end of the `<body>` tag


### [Clearing installed code snippets](https://www.framer.com/developers/custom-code#clearing-installed-code-snippets)
```
framer.setCustomCode({ 
  html: null,
  location: "bodyEnd" 
})
```

Setting the `html` value back to `null` clears the installed code snippet.
### [Reading Custom Code](https://www.framer.com/developers/custom-code#reading-custom-code)
Your plugin has the ability to detect if custom code was set by your plugin. Users also have the ability to disable custom code inserted by your plugin. When users disabled your Custom Code snippet, your plugin does not have the ability to re-enable the custom code.
You can however detect whether or not custom code was installed correctly.
```
const customCode = await framer.getCustomCode();
if (customCode.bodyStart.disabled) {
  // Custom  code was disabled by the user in settings.
  // Your plugin has no control over enabling this
  // But you could display some UI to indicate it.
}

const html = customCode.bodyStart.html
```

### [Subscribing to changes](https://www.framer.com/developers/custom-code#subscribing-to-changes)
If you want to update your UI when Custom Code is registered or when changes to the settings are made you can subscribe to changes.
```
import type { CustomCode } from "framer-plugin"
import { framer } from "framer-plugin"

function useCustomCode() {
    const [customCode, setCustomCode] = useState<CustomCode | null>(null)
    useEffect(() => framer.subscribeToCustomCode(setCustomCode), [])
    return customCode
}

function App() {
  const customCode = useCustomCode();
  // Render based on customCode value
}
```

