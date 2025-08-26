# [Component Examples](https://www.framer.com/developers/component-examples#component-examples)
Let's look at the very simplest component we could make. That would really just be a vanilla React button component. There really is no magic here, but it already works.
```
export default function Button(props) {
    return divHello</div
}
```

Let’s go a step deeper and add some styling. We can do this the standard React way too with `style`.
```
export default function Button(props) {
    const style = {
        display: "inline-block",
        backgroundColor: "orange",
        padding: 8,
    }

    return div style={style}Hello</div
}
```

Now, let’s make a title prop that is configurable from the interface (we will explain more about [property controls](https://www.framer.com/) later).
```
import { addPropertyControls, ControlType } from "framer"

export default function Button(props) {
    const style = {
        display: "inline-block",
        backgroundColor: "orange",
        padding: 8,
    }

    return div style={style}{props.text}</div
}

Button.defaultProps = {
    text: "My Title",
}

addPropertyControls(Button, {
    text: {
        title: "Text",
        type: ControlType.String,
    },
})
```

And there you have a simple configurable React component, right on the canvas. But I hope you can see how you can use the same concepts to build any React component you like. title prop that is configurable from the interface (we will explain more about [property controls](https://www.framer.com/developers/property-controls) later).
