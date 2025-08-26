# Framer Code Components Documentation ## Component Examples Let's look at the very simplest component we could make. That would really just be a vanilla React button component. There really is no magic here, but it already works. ```javascript export default function Button(props) { return 
Hello
; } ``` Let’s go a step deeper and add some styling. We can do this the standard React way too with `style`. ```javascript export default function Button(props) { const style = { display: "inline-block", backgroundColor: "orange", padding: 8, }; return 
Hello
; } ``` Now, let’s make a title prop that is configurable from the interface (we will explain more about [property controls](../) later). ```javascript import { addPropertyControls, ControlType } from "framer"; export default function Button(props) { const style = { display: "inline-block", backgroundColor: "orange", padding: 8, }; return 
{props.text}
; } Button.defaultProps = { text: "My Title", }; addPropertyControls(Button, { text: { title: "Text", type: ControlType.String, }, }); ``` And there you have a simple configurable React component, right on the canvas. But I hope you can see how you can use the same concepts to build any React component you like. ### Navigation - [Previous: Introduction](./components-introduction) - [Next: Sharing](./component-sharing)
