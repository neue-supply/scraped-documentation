[Reference](https://www.framer.com/developers/reference)
setRedirectOrder
# setRedirectOrder
### setRedirectOrder
Sets the order of the Redirects in the list
```
await framer.setRedirectOrder([aboutPageRedirect.id, blogPageRedirect.id]);
```

### [Parameters](https://www.framer.com/developers/reference/plugins-redirects-set-redirect-order#parameters)
  * `redirectIds: string[]` – An array of Redirect IDs representing the desired order.


### [Returns](https://www.framer.com/developers/reference/plugins-redirects-set-redirect-order#returns)
  * `Promise<void>`


### [Errors](https://www.framer.com/developers/reference/plugins-redirects-set-redirect-order#errors)
  * When the current user does not have permission to edit Site Settings, a `FramerPluginError` is thrown. See the [Permissions guide](https://www.framer.com/developers/plugins-permissions) to for more details.
  * When the current Project is not on a Plan that includes Redirects, a `FramerPluginError` is thrown. Also Framer will show a modal that asks the user to upgrade it's Plan.


### [Caveats](https://www.framer.com/developers/reference/plugins-redirects-set-redirect-order#caveats)
  * Unknown Redirect IDs are ignored.


