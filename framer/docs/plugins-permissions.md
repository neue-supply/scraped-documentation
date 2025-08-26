# [Permissions](https://www.framer.com/developers/plugins-permissions#permissions)
Plugins can do only what the user can. In turn, users’ abilities depend on the [granular project permissions](https://www.framer.com/help/articles/member-roles-and-permissions/) given to them. Plugins, however, can’t see the state of these permissions themselves. The only way of probing a user’s abilities is to check if the method of interest is allowed to be called or not.Permissions are always gated on an application level to ensure your Project is safe. However some Plugins may need to adjust their interfaces or ensure they can gracefully fail when an API call to fail due to missing permissions. 
If your Plugin is built with React, we recommend :
```
function AddTextButton() {
  const isAllowed = useIsAllowedTo("addText")
  
  const onClick = () => {
    framer.addText("Hello!")
  }
  
  return button disabled={!isAllowed} onClick={onClick}+</button
}
```

If not, use `subscribeToIsAllowedTo[](https://www.framer.com/developers/reference/plugins-subscribe-to-is-allowed-to)`. Here’s a vanilla JavaScript example:
```
element.onclick = () => framer.addText("Hello!")
element.disabled = !framer.isAllowedTo("addText")

const unsubscribe = framer.subscribeToIsAllowedTo(
  "addText",
  (isAllowed) => { element.disabled = !isAllowed }
)
```

You might’ve noticed in the code block above as well. It’s the backbone of Permissions API, but we recommend steering clear of it **when possible**. As permissions can change at any moment, reacting to those changes results in a much better user experience. Using it for initializing state is the only case where it’s unavoidable, but, it might also be the more ergonomic choice in event handlers:
```
async function onSomeNonUserInterfaceEvent() {
  const data = await fetch("https://example.com/data.json").json()
  if (!data.text) return

  if (framer.isAllowedTo("addText")) {
    framer.addText(data.text)
  } else {
    framer.notify("Not allowed to add text")
  }
}
```

All three - `useIsAllowedTo`, `subscribeToIsAllowedTo`, `isAllowedTo` - can take more than one argument, in which case the resulting boolean will be `true` only if **all** of the supplied methods are allowed:
```
const isAllowedToDoBoth = useIsAllowedTo("addText", "addImage")
```

If the method you’re interested in is on a class instance, like [Collection Item’s ](https://www.framer.com/developers/reference/plugins-collection-item-remove), then you can reference it by prefixing it with the name of the class:
```
const isAllowedToRemoveItems = useIsAllowedTo("CollectionItem.remove")
```

Many methods are currently available to users even without any permissions. As a rule of thumb, most of them start with `get`, but not all. If you start typing a method as an argument in one of the functions above and your editor doesn’t offer to auto-complete it, then it’s an always-allowed method. We also export `ProtectedMethod`, the type used by these functions for their parameters, if you’re going for a more complex permission setup:
```
const syncMethods = [
  "ManagedCollection.removeItems",
  "ManagedCollection.addItems",
  "ManagedCollection.setPluginData",
] as const satisfies ProtectedMethod[]
```

A `FramerPluginError` will be thrown if your Plugin attempts to execute a method that’s not available to the user, and a toast will be presented saying “Insufficient permissions, you need X”, where X is the required granular project permissions, e.g., “Design or Content”.
For those with Framer Beta access, you can test your Plugin’s handling of permissions by creating a second Framer user and inviting them to the same project as you. If you aren’t a part of any project or workspace on a Business plan, then please reach out to us at [creators@framer.com](https://creators@framer.com) and we will invite you to a special testing project. **Tip:** If your primary email is `jane@example.com`, you can register with `jane+test@example.com` and you’ll still receive emails sent to it in `jane@example.com`.
