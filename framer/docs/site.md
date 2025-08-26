# [Working with Sites](https://www.framer.com/developers/site#working-with-sites)
Plugins are able to view information about the published website, such as the time of the most recent deploy, or the url of the current page. This can be useful for creating plugins like SEO analyzers, and much more.
### [Using Published Site Information](https://www.framer.com/developers/site#using-published-site-information)
This information can be accessed via the `framer` API, using functions that follow the similar pattern to most of the top level Framer APIs. `getPublishInfo()` is an async function that returns `PublishInfo`. You can also subscribe to changes with `subscribeToPublishInfo()`. 
#### [`**PublishInfo**`](https://www.framer.com/developers/site#publishinfo)
Publish info provides information about both `staging` and `production` environments. Either of these may be `null`, if the site has never been published. Within each of those properties is the `Publish` data.
```
export type OptimizationStatus = "optimizing" | "optimized" | "error"

export interface Publish {
    deploymentTime: number
    optimizationStatus: OptimizationStatus
    url: string
    currentPageUrl: string
}
```

Here is the `PublishInfo` subscription abstracted into a hook that will always have the latest values.
```
function usePublishInfo() {
  const [publishInfo, setPublishInfo] = useState<PublishInfo>()

  useEffect(() => {
    return framer.subscribeToPublishInfo(setPublishInfo)
  }, [])

  return publishInfo
}
```

### [Example: Page Preview](https://www.framer.com/developers/site#example-page-preview)
An example usage of this could be rendering a preview of the current page in an iframe. To do that you can use the hook and pass the staging or production URL info the iframe.
```
const publishInfo = usePublishInfo()
const stagingUrl = publishInfo?.staging?.currentPageUrl
  
if (!stagingUrl) return "Publish your Site"

return (
  iframe src={stagingUrl} />
)
```

