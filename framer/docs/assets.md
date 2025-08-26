# [Working with Images](https://www.framer.com/developers/assets#working-with-images)
There is a collection of top level functions provided for adding and manipulating images in Framer.
### [Adding Images to the canvas](https://www.framer.com/developers/assets#adding-images-to-the-canvas)
To add an image to the canvas you use the `addImage` method.
```
// Upload an image with a URL
await framer.addImage({
  image: "https://example.com/image.png",
  name: 'My image',
  altText: "Alt description"
})

// Add an image through a file input
const fileInput = document.querySelector(`input[type="file"]`)
const file = fileInput.files[0]

const image = await framer.addImage({
  image: file, 
  name: "Uploaded image", 
  altText: "Alt Description" 
})

// or use the shorthand
const image = await framer.addImage(file)
```

### [Setting an image on the selected node](https://www.framer.com/developers/assets#setting-an-image-on-the-selected-node)
To add an image to the current selection you can use the `setImage` method.
```
await framer.setImage({ image: "https://example.com/image.png", altText: "Alt Description" })
```

This will apply the image to the current selected Node if it supports setting an image. If a Component Node is selected with a single Image control prop, it will also set the image.
### [Image resolution](https://www.framer.com/developers/assets#image-resolution)
All image-related methods allow you to set the resolution to `"auto"` (default), `"lossless"`, `"small"`, `"medium"`, `"large"` or `"full"`, same as through the UI. Effects of each are described in [this help article](https://www.framer.com/help/articles/image-resolution-options/).
```
await framer.addImage({ image: "https://example.com/image.png", resolution: "lossless" })
```

### [Uploading images without assigning them to a node](https://www.framer.com/developers/assets#uploading-images-without-assigning-them-to-a-node)
You can also upload images to framer without assigning them to a node on the canvas. The API looks similar.
```
const image = await framer.uploadImage({
  image: 'https://example.com/image.png',
  name: 'My image',
  altText: "alt Description"
})

// Later, use the image for creating a node
await framer.createFrameNode({
  backgroundImage: image
})
```

### [Getting an image from selection](https://www.framer.com/developers/assets#getting-an-image-from-selection)
The simplest way to get an image is to use the `getImage()` function. This will get the image of the current selection if it exists. An example usage looks like this:
```
const image = await framer.getImage();
```

To listen to image changes, you can use the `subscribeToImage` listener. Here is that abstracted into a hook.
```
import { framer, ImageAsset } from 'framer-plugin'

function useImageSelection() {
    const [image, setImage] = useState<ImageAsset | null>(null)
    useEffect(() => {
        return framer.subscribeToImage(setImage)
    }, [])
    return image
}
```

### [Modifying the alt text of an image](https://www.framer.com/developers/assets#modifying-the-alt-text-of-an-image)
In some cases you may want to modify the alt text of an Image without changing the image.
```
const imageNodes = await framer.getNodesWithAttributeSet("backgroundImage")
for (const imageNode of imageNodes) {
    if (!imageNode.backgroundImage) continue

    await imageNode.setAttributes({
        backgroundImage: imageNode.backgroundImage.cloneWithAttributes({
          altText: "Updated Alt Text"
        }),
    })
}
```

### [Example:](https://www.framer.com/developers/assets#example-image-processing)
Some plugins may be designed to manipulate images. For these cases, we provide raw image bytes and some utilities to perform image manipulation. A convenient way to perform image manipulation is by rendering the Image bitmap on a HTML canvas. An example implementation of bytesFromCanvas can be found in[ this gist](https://gist.github.com/huntercaron/6cd9b38229ea06255de7a79a257308d7).
```
// Get the selected image in framer
const image = await framer.getImage()

const canvas = document.createElement("canvas")
const ctx = canvas.getContext("2d")

// Load the image bytes into an ImageBitmap that canvas supports
const bitmap = await image.loadBitmap()

// Set the height of the canvas to the height of the image
ctx.canvas.width = img.width;
ctx.canvas.height = img.height;

// Here we horizontally invert the image bitmap.
ctx.scale(-1, 1);
ctx.drawImage(bitmap, -bitmap.width, 0);

const result = await bytesFromCanvas(canvas);

await framer.addImage({
  image: { bytes: result, mimeType },
});
```

## [Working with Files](https://www.framer.com/developers/assets#working-with-files)
Code components can be configured to accept files by adding `ControlType.File` to the component's property controls. A Plugin can upload files to Framer and assign them to the component's controls using the following code.
```
const uploadedFile = await framer.uploadFile({
  // You can also pass "File" objects
  // To accept <input type="file" /> inputs.
  file: "https://example.com/video.mp4",
  name: "Example Video" 
})

// Insert a Video Component with the uploaded file
await framer.addComponentInstance({
  url: "https://framer.com/m/framer/Video.js#Video",
  attributes: {
    controls: {
      srcType: "Upload",
      srcFile: uploadedFile,
    },
  },
})
```

## [Working with SVGs](https://www.framer.com/developers/assets#working-with-svgs)
Adding an SVG uses the `addSVG` async function. You can pass in the html for the SVG itself, along with a name of your choosing. Only SVG smaller than 4kb is accepted.
```
await framer.addSVG({
  svg: `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20"><path d="M5 2.5h10v5h-5Zm0 5h5l5 5H5Zm5 5v5l-5-5Z"/></svg>`,
  name: "framer.svg",
})
```

If you need to pass SVG bigger than 4kb, you should pass it's bytes data using the `addImage` function.
```
await framer.addImage({
  image: {
    type: "bytes",
    bytes: new TextEncoder().encode(svgInput),
    mimeType: "image/svg+xml",
  },
  name: "SVG",
});
```

