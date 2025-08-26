# [Override Examples](https://www.framer.com/developers/overrides-examples#override-examples)
There are a few common use cases for Overrides, below you’ll find examples on how to implement them. The code will vary slightly in your specific usage.
### [Custom IDs and Attributes](https://www.framer.com/developers/overrides-examples#custom-ids-and-attributes)
You can also use overrides to add custom IDs and data attributes to elements. For example if you want to add a `data-xx` or `id` tag to elements.
```
import { forwardRef, type ComponentType } from "react"

export function withTags(Component): ComponentType {
    return forwardRef((props, ref) => {
        return Component ref={ref} {...props} id="SomeID" data-framer="5678" />
    })
}
```

We don’t recommend to override core attributes like `class` or `className` as Framer relies on those and it will result in breaking styling. If you must, we recommend concatenating with the existing `class` value. 
### [Click Tracking](https://www.framer.com/developers/overrides-examples#click-tracking)
A popular use-case for Overrides is click tracking, you can do this quite simply. This depends on your tracking setup, but generally includes a call to a tracking API on click. Another way to do tracking is to add a data attribute to the layer (see above example) and adding a head script to your page in the Custom Code that performs the tracking.
```
import type { ComponentType } from "react";

export function withButtonTracking(Component): ComponentType {
    return forwardRef((props, ref) => {
      
        const handleClick = () => {
          // Call to tracking API
          void fetch("api.example.com/tracking/button")

          // Call normal onClick event if exists
          props?.onClick() 
        }
      
        return Component ref={ref} {...props} onClick={handleClick} />
    })
}
```

### [Text Content](https://www.framer.com/developers/overrides-examples#text-content)
Sometimes you want to dynamically replace text contents for any text element. You can use the `text` property to pass in any text content. The preview or published site will now show “Hello World”. However in many cases you can use [Fetch](https://www.framer.com/) for this instead.
```
import type { ComponentType } from "react";

export function withText(Component): ComponentType {
    return forwardRef((props, ref) => {
        return Component ref={ref} {...props} text="Hello World" />
    })
}
```

## [Application State](https://www.framer.com/developers/overrides-examples#application-state)
Application state refers to the data flow within your app, specifically how elements communicate with each other. This example has two Overrides to connect a button to a counter. Create an Override file with the following code and set up a similar layout. Then, connect the two overrides: attach withIncrement to the button and withCount to the text field of the counter. Please note that if you want to build a "real app" that creates, updates, and lists dynamic data, consider using a simple React application or a no-code app builder if you don't know how to code.
```
import type { ComponentType } from "react"
import { createStore } from "https://framer.com/m/framer/store.js@^1.0.0"

const useStore = createStore({ count: 0 })

export const withCount = (Component): ComponentType => {
    return forwardRef((props, ref) => {
        const [store, setStore] = useStore()
        return Component ref={ref} {...props} text={`${store.count}`} />
    }
}

export const withIncrement = (Component): ComponentType => {
    return forwardRef((props, ref) => {
        const [store, setStore] = useStore()
        const onTap = () => setStore({ count: store.count + 1 })
        return Component ref={ref} {...props} onTap={onTap} />
    })
}
```

