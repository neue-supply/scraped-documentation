[Reference](https://www.framer.com/developers/reference)
addRedirects
# addRedirects
Add Redirects to your project.
```
await framer.addRedirects([
  { from: "/business", to: "/enterprise", expandToAllLocales: true },
])
```

### [Parameters](https://www.framer.com/developers/reference/plugins-redirects-add-redirects#parameters)
  * `redirects: CreateRedirect[]` – An array of objects representing the Redirects to add.
    * `from[](https://www.framer.com/developers/reference/plugins-redirect-from): string` – The path to redirect from.
    * `to[](https://www.framer.com/developers/reference/plugins-redirects-redirect-to): string` - The path to redirect to.
    * `expandToAllLocales[](https://www.framer.com/developers/reference/plugins-redirect-expand-to-all-locales): boolean` - Whether to expand the redirect to all Locales.


### [Returns](https://www.framer.com/developers/reference/plugins-redirects-add-redirects#returns)
  * `Promise<Redirect[](https://www.framer.com/developers/reference/plugins-redirect)[]>` – The added Redirects.


### [Errors](https://www.framer.com/developers/reference/plugins-redirects-add-redirects#errors)
  * When the current user does not have permission to edit Site Settings, a `FramerPluginError` is thrown. See the [Permissions guide](https://www.framer.com/developers/plugins-permissions) for more details.
  * When the current Project is not on a Plan that includes Redirects, a `FramerPluginError` is thrown. Also Framer will show a modal that asks the user to upgrade it's Plan.
  * When the Project Redirects reach the maximum allowed count, a `FramerPluginError` is thrown. Currently Framer allows up to **2500** Redirects per Project.


It's possible to use some basic regular expressions in Redirects.
`from` paths can contain wildcards, which will match any string. For example, you can redirect all pages under `/faq/` to a new `/support` page by doing the following:
```
await framer.addRedirects([
  { from: "/faq/*", to: "/support", expandToAllLocales: false },
  { from: "/business", to: "/enterprise", expandToAllLocales: true },
])
```

It is also possible to capture those regular expression groups and pass them through to the `to` path. For example, if you moved your blog from `/posts` to `/blog` and wanted existing links to keep working, then you can do the following:
```
await framer.addRedirects([
  { from: "/posts/*", to: "/blog/:1", expandToAllLocales: false },
])
```

This would, for example, redirect `/posts/getting-started` to `/blog/getting-started`.
