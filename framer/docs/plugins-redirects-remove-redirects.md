[Reference](https://www.framer.com/developers/reference)
removeRedirects
# removeRedirects
### removeRedirects
Remove Redirects from your project.
```
await framer.removeRedirects([aboutPageRedirect.id, blogPageRedirect.id])
```

### [Parameters](https://www.framer.com/developers/reference/plugins-redirects-remove-redirects#parameters)
  * `redirectIds: string[]` – An array of Redirect IDs to remove.


### [Returns](https://www.framer.com/developers/reference/plugins-redirects-remove-redirects#returns)
  * `Promise<void>`


### [Errors](https://www.framer.com/developers/reference/plugins-redirects-remove-redirects#errors)
  * When the current user does not have permission to edit Site Settings, a `FramerPluginError` is thrown. See the [Permissions guide](https://www.framer.com/developers/plugins-permissions) to for more details.
  * When the current Project is not on a Plan that includes Redirects, a `FramerPluginError` is thrown. Also Framer will show a modal that asks the user to upgrade it's Plan.


### [Caveats](https://www.framer.com/developers/reference/plugins-redirects-remove-redirects#caveats)
  * Unknown Redirect IDs are ignored.


