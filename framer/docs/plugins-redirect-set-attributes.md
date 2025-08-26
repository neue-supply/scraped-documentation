[Reference](https://www.framer.com/developers/reference)
[Redirect](https://www.framer.com/developers/reference/plugins-redirect)
setAttributes
# setAttributes
### setAttributes
Set the attributes of a Redirect.
```
await redirect.setAttributes({ from: "/new-url" }
```

### [Parameters](https://www.framer.com/developers/reference/plugins-redirect-set-attributes#parameters)
  * `attributes: Partial<CreateRedirect>` – The updated attributes and their new values.


### [Returns](https://www.framer.com/developers/reference/plugins-redirect-set-attributes#returns)
  * `Promise<Redirect[](https://www.framer.com/developers/reference/plugins-redirect) | null>`


### [Errors](https://www.framer.com/developers/reference/plugins-redirect-set-attributes#errors)
  * When the current user does not have permission to edit Site Settings, a `FramerPluginError` is thrown. See the [Permissions guide](https://www.framer.com/developers/plugins-permissions) to for more details.
  * When the current Project is not on a Plan that includes Redirects, a `FramerPluginError` is thrown. Also Framer will show a modal that asks the user to upgrade it's Plan.


